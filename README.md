
Namespace Class Loader for Contao 3
===================================

This extension implements a valid PSR-0 class loader for Contao 3.
The implementation is based on the `Composer\Autoload\ClassLoader`.

**This extension is outdated, see the Upgrade information!**


### Usage

Place all files in `system/modules/_autoload` in your Contao installation.

Usage works similar to the Contao class loader, except that you do not 
need to include every class file if you follow PSR-0 standards. Use the
following example to implement the class loader in your `config/autoload.php`:

```php
<?php

/**
 * Register namespace
 */
NamespaceClassLoader::add('Isotope', 'system/modules/isotope/library');

```


### Upgrade to Contao 4

In Contao 4, the only way to install extensions is using Composer.
Therefore, you will not need this extension but should use Composer's
class loader.

To be compatible with Contao 3 extension repository and Contao 4,
you will need to require at least Contao 3.3 and set it up as follow:

 1. Define your [namespaces or classes in `composer.json`][1].
 2. Remove the dependency for `terminal42/contao-namespace-class-loader`
    from your `composer.json`
 3. Keep the dependency in the old Extension Repository
 4. Make `_autoload` an optional dependency in your `autoload.ini` like
    so:
    
        requires[] = "*_autoload"

 5. Only call `NamespaceClassLoader` in your `autoload.php` if the 
    class is actually available:
    
        if (class_exists('NamespaceClassLoader')) {
            NamespaceClassLoader::add( ... );
        }


If the extension is installed via Composer, the classes will be loaded
by the Composer autoloader. When installed using the old extension
repository, the `_autoload` extension will be added and the classes
will work like before.

See [our commit][2] on how we accomplished this in [Isotope eCommerce][3].
 
 
[1]: https://getcomposer.org/doc/04-schema.md#autoload
[2]: https://github.com/isotope/core/commit/3f418a50ea81138834e72d9e978bbc196e63a9b2
[3]: https://isotopeecommerce.org
