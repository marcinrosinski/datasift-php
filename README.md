DataSift API
============

This is the official PHP library for accessing [Datasift](http://www.datasift.net/). See the examples
folder for some simple example usage. Full documentation is in the doc folder.

The unit tests should be run with phpunit.

Simple example
--------------

This example looks for anything that contains the word "datasift" and simply
prints the content to the screen as they come in.

```php
<?php
  require 'lib/datasift.php';
  $user = new DataSift_User('your username', 'your api_key');
  $def = $user->createDefinition('interaction.content contains "datasift"');
  $consumer = $def->getConsumer(DataSift_StreamConsumer::TYPE_HTTP,
                function($consumer, $data) {
                  echo $data['interaction']['content']."\n";
                });
  $consumer->consume();
?>
```

Requirements
------------

* PHP 5
* JSON (included in PHP 5.2+, otherwise use http://pecl.php.net/package/json)
