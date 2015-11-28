#Integrating J2Store in your component

* **[Introduction](#introduction)**
* **[The concept](#concept)**
* **[Integrating with your component](#integration)**
  * **[Get the product form fields](#getform)**
  * **[Save product data](#savedata)**
  * **[Display the cart](#displaycart)**

<a name="introduction"></a>
##Introduction

Integrating J2Store with your extension is pretty straightforward. Since Version 3, we implement a flexible Plugin API and the entire
J2Store core is re-written from scratch using the Framework on Framework (FOF).

<a name="concept"></a>
##The Concept

J2Store can treat any item (an article, an event, a photo) as a product. All it needs is the name of the source (read as your component's name. Example: com_foo) and the source item's ID. 
You can use your component's plugin events to display the J2Store's Product Form, Save it and then Render it (in the front end)
So basically three events are sufficient to integrate J2Store in your component.

Let me give you an example of how J2Store is integrated with the Joomla articles

1. onContentPrepareForm

Here we inject the J2Store's Product Form into the Article's Edit view. So the store owner treats the article as product and fills in the form.

2. onContentAfterSave
Here, we catch the data of the filled-in product form and save it to the J2Store's tables. While saving, we save two important variables
1. product_source = The name of the component which serves as the catalog source. In this case, com_content
2. product_source_id = The id of the item that is treated as a product. In this case, the article id.

3. onContentAfterDisplay
So, we have displayed the form, saved the data. Now it is time to inject the cart block (price, quantity field, Add to cart button) into the article.
This method takes care of it.

<a name="integration"></a>
##Integrating with your component

Let us now integrate J2Store with your component
>NOTE: You should be good with the Joomla Plugin concept to carry out the integration. I assume that you have a good understanding of plugin events

<a name="getform"></a>
### Get the product form fields
The first and foremost task is to get the J2Store's Product form fields to display inside your component's item.

If your component fire's an event after displaying the form, then the task is pretty easy. You can create a system plugin with the event and call the following lines
```php
   $app = JFactory::getApplication();
   //the id of your item. This will be treated as the product_source_id
	 	$id = $app->input->getInt('cid');

	 	$productTable = F0FTable::getAnInstance('Product' ,'J2StoreTable');
			
		$productTable->load(array('product_source'=>'com_foo', 'product_source_id' =>$id));

		$product_id = (isset($productTable->j2store_product_id)) ? $productTable->j2store_product_id : '';

	 	$inputvars = array(
	 			'task' =>'edit',
	 			'render_toolbar'        => '0',
	 			'product_source_id'=>$id,
	 			'id' =>$product_id,
	 			'product_source'=>'com_foo',
	 			'form_prefix'=>''
	 	);
	 	$input = new F0FInput($inputvars);

	 	@ob_start();
		F0FDispatcher::getTmpInstance('com_j2store', 'product', array('layout'=>'form', 'tmpl'=>'component', 'input' => $input))->dispatch();
		$html = ob_get_contents();
		ob_end_clean();
		return $html;
```
<a name="savedata"></a>
###Save the product data

Saving the data is also very simple. Just capture the filled-in form data (Usually in your After Save event)
Then just pass the data (can be either an array or an object) to
```php
F0FModel::getTmpInstance('Products', 'J2StoreModel')->save($data);
```

>IMPORTANT: The array or object should contain have the product_source and product_source_id .

Example:
```php
product_source='com_foo'
product_source_id=$id //the ID of your item
```

<a name="displaycart"></a>
###Display the cart block

Time to get the add to cart block for your item.
Here are the three lines that will get you the entire cart block.

```php
$html = '';
$product = F0FTable::getAnInstance ( 'Product', 'J2StoreTable' )->getClone ();
if ($product->get_product_by_source ( 'com_foo', $id )) {
		$html = $product->get_product_html();
	}
	echo $html;
```	

You have a number of methods in the product object.

To get the main image
```php
$product->get_product_images_html('main');
```
To get cross sell products
```php
$product->get_product_cross_sells_html();
```
To get up sell products

```php
$product->get_product_upsells_html();
```

Refer the the content plugin of J2Store for more detailed information and methods of implementing.
(plugins/content/j2store/j2store.php)
