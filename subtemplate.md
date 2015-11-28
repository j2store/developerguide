#Sub templates

Since Version 3, J2Store comes with a sub-templating system that is very similar to the K2 content construction kit's system. 
Sub-templates allows store owners to have finer control over their product layouts. They can move the pieces around and have a unique 
design for their store front.

> IMPORTANT: Sub-templates work only with J2Store Product List Layout. They will not work with any other layouts.

##Default sub-templates

The J2Store package by default comes with two sub-templates

1. Default (supports Bootstrap 2)
2. Bootstrap3 (supports Bootstrap 3)

The sub-templates are located in the following location: /components/com_j2store/templates 

You can take one of these as your base to create your own sub-template. The best way is by copying an existing sub-template

##Creating a sub-template

Let us create a sub-template called: foo

#### Step 1:
Using a FTP client or your hosting cpanel's File manager, go to /components/com_j2store/templates

Copy the **default** folder (copy the entire folder)

to

/templates/<YOUR_TEMPLATE>/html/com_j2store/templates/default

####Step 2:

Now go to /templates/<YOUR_TEMPLATE>/html/com_j2store/templates/ folder

You will see the folder: default.

Rename it as: foo

####Step 3

Now go to /templates/<YOUR_TEMPLATE>/html/com_j2store/templates/foo

You will a list of files

1. files starting with default_* = controls the list view
2. files starting with view_* = controls the detail product view

There are four master files (one for each product type)
1. default_simple.php
2. default_configurable.php
3. default_variable.php
4. default_downlodable.php

Similarly, you will find the files for detail single product view (view_simple.php, view_configurable.php, view_variable.php and view_downlodable.php)

You will have to edit these files and organise your layout. These master files in turn will call child templates as well (which are common for many product types)


