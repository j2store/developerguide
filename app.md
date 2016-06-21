# App for J2Store

* **[Introduction](#introduction)**
* **[App Structure](#app_struct)**
* **[Naming Conventions](#naming)**
* **[The Manifest](#manifest)**
* **[Creating app class](#app_class)**
* **[ App Model Class](#model_class)**
* **[App controller](#controller)**

<a name="introduction"></a>
#### Introduction

Developing a app for J2Store is very simple process if you are good in PHP and the Joomla MVC structure.

J2Store comes with a app library and wrappers that makes creating a app for J2Store.

<a name="app_struct"></a>
#### App Structure
There is a folder structure and a few naming conventions, that should be followed during the development of a app for J2Store.

A typical app should look like this:
```
├── app_example/
│   ├── app_example.php
│   ├── app_example.xml
│   ├── languages/
│   │   ├── en-GB.plg_j2store_app_example.ini
│   ├── app_example/
│   │   ├── tmpl/
│   │   │   ├── form.php
│   │   │   ├── default.php
│   │   ├── controller.php
│   │   ├── models/
│   │   │   ├── appexample.php
```

<a name="naming"></a>
#### Naming Conventions

The name of the app folder should start with the prefix "**app_"**. Otherwise, J2Store will not recognise your app. So our example app is named as:
**app_example**

Make sure that the name of the file and folder is in lower case and there are no spaces or any other characters in the name.

<a name="manifest"></a>

#### Manifest

An example manifest should look like this:

```xml
<?xml version="1.0" encoding="utf-8"?>
<extension version="3.0" type="plugin" group="j2store" method="upgrade">
	<name>Example</name>
	<version>1.0</version>
	<creationDate>July 2015</creationDate>
	<author>J2Store</author>
	<authorEmail>supports@j2store.org</authorEmail>
	<authorUrl>http://www.j2store.org</authorUrl>
	<copyright>2015 Weblogicx India</copyright>
	<license>GNU General Public License v2</license>
	<description>PLG_J2STORE_APP_DONATION_DESC</description>
	<files>
		<filename plugin="app_example">app_example.php</filename>
		<folder>app_example</folder>
		<folder>languages</folder>		
		<filename>index.html</filename>
	</files>
	<languages>
		<language tag="en-GB">languages/en-GB.plg_j2store_app_example.ini</language>		
	</languages>
	<config>
		<fields name="params">
			<fieldset name="basic" label="J2STORE_BASIC_SETTINGS" 
				addfieldpath="/administrator/components/com_j2store/models/fields">		
			
			</fieldset>
		</fields>
	</config>		
</extension>
```
<a name="app_class"></a>
#### Creating app class

Make sure the name of the class suffix is same as your app file's name. And it should extend the J2StoreAppPlugin class.
```php
defined('_JEXEC') or die('Restricted access');
require_once(JPATH_ADMINISTRATOR.'/components/com_j2store/library/plugins/app.php');
class plgJ2StoreApp_Example extends J2StoreAppPlugin
{
	/**
	 * @var $_element  string  Should always correspond with the plugin's filename,
	 *                         forcing it to be unique
	 */
	var $_element    = 'app_example';
```

This file should have following two methods:

**onJ2StoreGetAppView** - This method is used to check if it is a app_example or not.

**viewList** - A controller for this plugin.
```php
$html = $this->_getLayout('default', $vars);
``` 
The above line will call the template layout for the app_example from /app_example/app_example/tmpl/default.php

<a name="model_class"></a>
#### App Model Class

App's model should have file named with appexample.php and it should be like below
```php
defined('_JEXEC') or die('Restricted access');
require_once (JPATH_ADMINISTRATOR . '/components/com_j2store/library/appmodel.php');
class J2StoreModelAppExample extends J2StoreAppModel
{

	public $_element = 'app_example';

}
```
<a name="controller"></a>
#### App controller

Controller.php file should be located in /app_donation/app_donation/controller.php and you must include the J2Store's library appcontroller and it should be written like below
```php
defined('_JEXEC') or die('Restricted access');
require_once(JPATH_ADMINISTRATOR.'/components/com_j2store/library/appcontroller.php');

class J2StoreControllerAppexample extends J2StoreAppController{

	var $_element   = 'app_donation';

}
```

