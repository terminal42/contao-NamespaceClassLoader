
Namespace Class Loader for Contao 3
===================================

This extension implements a valid PSR-0 class loader for Contao 3.
The implementation is based on the `Composer\Autoload\ClassLoader`.


### Installation ###

Place all files in `system/modules/_autoload` in your Contao installation.


### Usage ###

Usage works similar to the Contao class loader, except that you do not need to include every class file if you follow PSR-0 standards. Use the following example to implement the class loader in your `config/autoload.php`:

```php
<?php

/**
 * Register namespace
 */
NamespaceClassLoader::add('Isotope', 'system/modules/isotope/library');

```
