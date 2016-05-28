# Using Microsoft Azure with codeigniter

Hi, we doing my side projects with codeingiter and some of our clients use microsoft azure, we thought why not help
the community of codeigniters :)

> **note** this is the very intial phase of libraries, don't expect them to be perfect, we might tweak them in future

# Get started

1) download [codeigniter](https://www.codeigniter.com/)'s latest version

2) unzip it and do the usual

3) open `application/libary` and create one file name `composer.json` and paste the content of this [composer.json](https://github.com/Azure/azure-storage-php/blob/master/composer.json)

4) open terminal navigate to your codeingiter's directory and run `composer install` make sure you have composer in your system


> we have done all this hard work for you, if you want readymade stuff, you can simply download / clone this repo :)

# Using Library


1) you may autoload this library in codeigniter or you may load mannually on every controller, not we are not autoloading but if you wish please open `application/config/autoload.php`
```
/*
| -------------------------------------------------------------------
|  Auto-load Libraries
| -------------------------------------------------------------------
| These are the classes located in system/libraries/ or your
| application/libraries/ directory, with the addition of the
| 'database' library, which is somewhat of a special case.
|
| Prototype:
|
|	$autoload['libraries'] = array('database', 'email', 'session');
|
| You can also supply an alternative library name to be assigned
| in the controller:
|
|	$autoload['libraries'] = array('user_agent' => 'ua');
*/
$autoload['libraries'] = array('azurecdn');
```
**creating container**
```
$this->azurecdn->create_container("container-name");
// will return true or false
// valid container name https://msdn.microsoft.com/en-us/library/azure/dd135715.aspx
```
**uploading blob / file**
```
$blob_mime_type = $this->upload->data()['file_type']; // mime type of uploaded file on server
$set_blob_file_name = "my_first_college_day.jpg" // set the name of file
// for now, this file must be in server
$full_file_path = "http://mydomain.com/uploaded_images/my_first_college_day.jpg";
$blob_container = "college-uploads";
$this->azurecdn->upload_blob($full_file_path, $blob_file_name, $blob_container, $blob_mime_type);
```

# that's it

> this is still an early version, please help us or be patient :)

azure php sdk github repos

1) https://github.com/Azure/azure-storage-php

2) https://github.com/Azure/azure-sdk-for-php
