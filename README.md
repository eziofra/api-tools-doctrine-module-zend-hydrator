DoctrineModule zend-hydrator
============================

[![Total Downloads](https://poser.pugx.org/api-skeletons/zf-doctrine-module-zend-hydrator/downloads)](https://packagist.org/packages/api-skeletons/zf-doctrine-module-zend-hydrator)

** This is a Patch Repository **

Since the [laminas/laminas-stdlib](https://github.com/laminas/laminas-stdlib) hydrators were moved into their own repository, [laminas/laminas-hydrator](https://github.com/laminas/laminas-hydrator), the [DoctrineModule](https://github.com/doctrine/DoctrineModule) repository has not been updated to correctly use the new library.  Through many discussions on the issue [@doctrineorm](https://twitter.com/doctrineorm) continues to maintain they are in line with [laminas/laminas-hydrator](https://github.com/laminas/laminas-hydrator) because, very unusually, the new library was written to be backwards compatible with [laminas/laminas-stdlib](https://github.com/laminas/laminas-stdlib) but that backwards compatibility was removed from zend-hydrator in later versions leaving developers who want to use Doctrine in their projects which allow for custom hydrators out on a limb.

This library overrides the files from [DoctrineModule](https://github.com/doctrine/DoctrineModule) which are broken because they still reference [laminas/laminas-stdlib](https://github.com/laminas/laminas-stdlib) for their hydrators.

Discussion on this issue:
 * Jan 30, 2016: https://github.com/doctrine/DoctrineModule/pull/548
 * Apr 7, 2016: https://github.com/doctrine/DoctrineModule/pull/558#issuecomment-207212246


Installation
------------

Installation of this module uses composer. For composer documentation, please refer to
[getcomposer.org](http://getcomposer.org/).

```sh
$ php composer.phar require api-skeletons/zf-doctrine-module-zend-hydrator ^1.0
```

Inside your `composer.json` file this library must be included **before** [doctrine/doctrine-module](https://github.com/doctrine/DoctrineModule).  This ordering allows classes from this repository to override the DoctrineModule classes which are broken.


Installation Warnings
---------------------

You may receive the following warnings.  These are to be expected and are not a cause for concern.

```sh
Warning: Ambiguous class resolution, "DoctrineModule\Stdlib\Hydrator\DoctrineObject" was found in both "Projects/phpro/zf-doctrine-hydration-module/vendor/api-skeletons/zf-doctrine-module-zend-hydrator/src/DoctrineObject.php" and "/Projects/phpro/zf-doctrine-hydration-module/vendor/doctrine/doctrine-module/src/DoctrineModule/Stdlib/Hydrator/DoctrineObject.php", the first will be used.
Warning: Ambiguous class resolution, "DoctrineModule\Stdlib\Hydrator\Filter\PropertyName" was found in both "/Projects/phpro/zf-doctrine-hydration-module/vendor/api-skeletons/zf-doctrine-module-zend-hydrator/src/Filter/PropertyName.php" and "/Projects/phpro/zf-doctrine-hydration-module/vendor/doctrine/doctrine-module/src/DoctrineModule/Stdlib/Hydrator/Filter/PropertyName.php", the first will be used.
Warning: Ambiguous class resolution, "DoctrineModule\Stdlib\Hydrator\Strategy\AbstractCollectionStrategy" was found in both "/Projects/phpro/zf-doctrine-hydration-module/vendor/api-skeletons/zf-doctrine-module-zend-hydrator/src/Strategy/AbstractCollectionStrategy.php" and "/Projects/phpro/zf-doctrine-hydration-module/vendor/doctrine/doctrine-module/src/DoctrineModule/Stdlib/Hydrator/Strategy/AbstractCollectionStrategy.php", the first will be used.
```


When to use this Patch Repository
---------------------------------

If you are using custom hydrators for your entities and you see errors like the following, this repository will correct them.

```
Argument 2 passed to Laminas\Stdlib\Hydrator\AbstractHydrator::addStrategy() must be an instance of Laminas\Stdlib\Hydrator\Strategy\StrategyInterface ...
```


This is a Patch Repository
--------------------------

If you would like to be involved in the conversation at [DoctrineModule](https://github.com/doctrine/DoctrineModule) to help get [laminas/laminas-hydrator](https://github.com/laminas/laminas-hydrator) implemented correctly in [@doctrineorm](https://twitter.com/doctrineorm) repository you may contribute to the discussions linked above.


Appreciation
------------

Finding this patch would not have been possible without the constant support of [Toon Verwerft](https://github.com/veewee) and his [zf-doctrine-hydration-module](https://github.com/phpro/zf-doctrine-hydration-module).  It took nearly six months to find a solution and he supported [my](http://www.tomhanderson.com) efforts the whole time.  Thank you Toon!
