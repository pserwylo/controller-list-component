# ControllerList component for CakePHP

## Purpose

A simple component for CakePHP 2.x which returns a list of controllers and the corresponding action names.

## Requirements

Requires at least PHP 5.3.

## Installation

Copy the file `app/Controller/Component/ControllerListComponent.php` to the `Controller/Component` folder of your application.

## Usage

First, you have to add the component to the `$components` array of your controller(s):
```php
public $components = array('ControllerList');
```

Then you can use the component in your action(s) with: `$this->ControllerList->getList()`. You can also specify the controllers which should be excluded from the returned list: `$this->ControllerList->getList(array('UsersController'))`. Please note that without this parameter, the `PagesController` is automatically excluded.

The structure of the returned array is like:
```php
<?php
array(
  'ExampleController' => array(
    'name' => 'Example',
    'displayName' => 'Example',
    'actions' => array(
      (int) 0 => 'index',
      (int) 1 => 'show'
    )
  ),
  'VendorExampleController' => array(
    'name' => 'VendorExample',
    'displayName' => 'Vendor Example',
    'actions' => array(
      (int) 0 => 'index',
      (int) 1 => 'callback',
      (int) 2 => 'api'
    )
  )
)
```

### Configuration

The component provides two configuration options.

The first option, `includePlugins`, determines whether controllers in plugins are listed. By default, those controllers are ignored.
```php
public $components = array('ControllerList' => array('includePlugins' => true));
```

The second option, `parentControllers`, allows you to specify parent controllers other than `AppController`.
```php
public $components = array('ControllerList' => array('parentControllers' => array('ParentController')));
```

## Changes

### v2.0.2 (2016-01-11)

* Added the configuration option `includePlugins`. Thanks to [Oscar](https://github.com/oscar-ol)!

### v2.0.1 (2015-11-18)

* Added the configuration option `parentControllers`. Thanks to [leodisarli](https://github.com/leodisarli)!

### v2.0.0 (2012-07-30)

* Added parameter `$controllersToExclude` to the `getList()` method
* Changed the structure of the returned array by including the keys `name`, `displayName` and `actions`. Thanks to [Charles A. Beasley](https://github.com/carmelchas)!

### v1.0.0 (2012-01-29)

* Adapted for CakePHP 2.x. Thanks to [Paolo Iulita](https://github.com/paoloiulita)!

### 2010-06-29

* Initial release

## Contact

If you have questions or feedback, feel free to contact me via Twitter ([@dhofstet](https://twitter.com/dhofstet)) or by email (daniel.hofstetter@42dh.com).

## License

The ControllerList component is licensed under the MIT license.
