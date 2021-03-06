#Introduction
> Only for template developers. Read further on only if you are a template developer and familiar with the Joomla template system.

J2Store is a light-weight, flexible shopping cart with tonnes of features. The most interesting feature for template developers is: It supports sub-templates. Its layouts are clean and anyone can understand by just seeing it. The code is well-commented and you can almost read it like a book.
This guide servers as a starting point for integrating J2Store with your template and add support for it.

* **[Download and Install J2Store](#download_install_j2store)**
    * **[Download J2Store](#download_j2store)**
    * **[Install J2Store](#install_j2store)**
    * **[J2Store Configuration](#j2store_configure)**
* **[Choose Layout to display your products](#choose_layout)**
    * **[J2Store Product List View](#j2store_layout)**
    * **[Joomla Category Blog Layout](#article_layout)**
    * **[Create Product](#create_product)**
* **[J2Store File Location and override procedure](#file_override_location)**
    * **[Layout file location](#layout_file)**
    * **[Frontpage product listing files](#product_listing)**
    * **[Product view](#product_view)**
    * **[File location of filter](#product_filter)**
    * **[Cart page](#cart)**
    * **[Checkout page](#checkout)**
    * **[Order history page](#myprofile)**


<a name="download_install_j2store"></a>
##Download and Install J2Store

<a name="download_j2store"></a>
####Download J2Store

1. Grab the J2Store package from our website http://j2store.org/

2. Become an affiliate ! You can start earning a handsome 30% for each of your referral sale.  http://j2store.org/affiliate-programme

<a name="install_j2store"></a>
####Install J2Store

1. Use the Joomla installer to install the J2store package.

2. Go to Joomla Extension > Manage > Install

3. Choose and select your file.

4. Click Upload & Install.
![](./assets/images/j2store_install.png)

<a name="j2store_configure"></a>
####J2Store Configuration

1. Once installed, you will get J2store in the Joomla component list and also separate J2store tab in Joomla backend.
![](./assets/images/j2store_component.png)

2. Now, Go to J2store > Dashboard.

3. Fill all the fields in the basic settings and click Save & Proceed.
![](./assets/images/j2store_basic_settings.png)

<a name="choose_layout"></a>
## Choose Layout to display  products

J2Store uses the default Joomla articles as products. So an article can be a product. That means you can use the Category blog, Single article layout for showcasing products.

We also provide an awesome Product List Layout with a lots of controls. And it supports the sub-template concept like the K2. You can create any number of sub-templates and each can have a unique style.

For example, the store front has two categories: Fruits, Vegetables.
You can create a sub-template for fruits and set its own styles.
You can create another sub-template for Vegetables and it can have its own styles.
The possibilities are limitless.

By default, j2store comes with two sub-templates
1. Default - This is based on the Bootstrap 2.x
2. Bootstrap 3 - As the name says, this supports the Bootstrap 3 markup.

So you can build you sub-template by copying one of these.


<a name="j2store_layout"></a>
####J2Store Product List View

It is very easy and flexible to display the product in frontend using J2Store Layout. Please follow the procedure given below.

1. Go to Menu manager -> Main menu and create a new menu item.

2. Give the menu title and choose the menu type as **J2store > Product List View**
![](./assets/images/j2store_layout.png)

3. Choose the Category which have chosen when creating product. The category added in the product and the category added in the menu should be same.
![](./assets/images/j2store_menu.png)

4. In the menu you can see these three tabs **common options, Item view options in category listings, Item view options**.

 **Common Options:** Here you can choose the layout(bootstrap 2, bootstrap 3).

 **Item view options in category listings:** Here you can choose which are the things should be displayed in product pages. For example, you can hide / show price, images, filters, etc..

 **Item view options:** Here you can choose which are the things should be displayed in product view page.

<a name="article_layout"></a>
####Joomla Category Blog Layout

This is the another method / way / layout to display your products. By using this layout, you can use the Joomla's native article options.

1. Go to Menu manager -> Main menu and create a new menu item.

2. Give the menu title and choose the menu type as **Articles -> Category Blog**

<a name="create_product"></a>
####Create Product

1. Since J2Store uses the default Joomla articles as its products, it lets you use native content as product.

2. Go to Content > Articles > Add new article. Now, new article page will open.

3. Give the title of the product, add your description about the product in the content tab and choose the category in which you want to display the product(category chosen here and category chosen in the menu should be same).
![](./assets/images/j2store_create_product.png)

4. Now, go to J2store Cart tab, choose **YES** to treat article as a product then choose your **Product Type** from the list(Simple, Variable, Configurable, Downloadable) and then click **Save and Continue**.
![](./assets/images/j2store_product_type.png)

5. After saving, again go to J2store cart tab. Now you can see the options to add image for product, set prices, add filters / Tax / Shipping.
![](./assets/images/j2store_product_settings.png)

<a name="file_override_location"></a>
##J2Store File Location and override procedure

<a name="layout_file"></a>
####Layout file location

Go to /components/com_j2store/templates which contains two folders named **bootstrap3** and **default**(bootstrap2).

If you choose bootstrap3 as sub-template then you have to go with bootstrap3 folder.

If you choose default as sub-template then you have to go with default folder.

<a name="product_listing"></a>
####Frontpage product listing files

Open your sub-template folder(/components/com_j2store/templates/YOUR-SUB-TEMPLATE) where you can find the files with name started with default_(for example, default_simple.php, default_images.php, etc). Those files controls all the features displaying in the category listing page.
![](./assets/images/template_guide_product_detail.png)

**OVERRIDE PATH**
templates/YOUR-TEMPLATE/html/com_j2store/templates/YOUR-SUB-TEMPLATE/

<a name="product_view"></a>
####Product view

Open your sub-template folder where you can find the files with name started with view_(for example, view_simple.php, view_images.php, view_options.php, view_notabs.php, etc). Those files controlled all the features displaying in the Product view page.
![](./assets/images/template_guide_product_view.png)

**OVERRIDE PATH**
templates/YOUR-TEMPLATE/html/com_j2store/templates/YOUR-SUB-TEMPLATE/

<a name="product_filter"></a>
####File location of filter

Following files controls filter section,

/components/com_j2store/templates/YOUR-SUB-TEMPLATE/default_filters.php

/components/com_j2store/templates/YOUR-SUB-TEMPLATE/default_sortfilter.php

**OVERRIDE PATH**
templates/YOUR-TEMPLATE/html/com_j2store/templates/YOUR-SUB-TEMPLATE/

<a name="cart"></a>
####Cart page

Cart page is controlled by the files located in the follwing path /components/com_j2store/views/carts/tmpl
![](./assets/images/template_guide_cart.png)

**OVERRIDE PATH**
templates/YOUR-TEMPLATE/html/com_j2store/carts/

<a name="checkout"></a>
####Checkout page

Checkout is controlled by the files located in the follwing path /components/com_j2store/views/checkout/tmpl
![](./assets/images/template_guide_checkout.png)

**OVERRIDE PATH**
templates/YOUR-TEMPLATE/html/com_j2store/checkout/

<a name="myprofile"></a>
####Order history page

Order history page is controlled by the files located in the follwing path
/components/com_j2store/views/myprofile/tmpl
![](./assets/images/template_guide_myprofile.png)

**OVERRIDE PATH**
templates/YOUR-TEMPLATE/html/com_j2store/myprofile/