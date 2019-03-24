# Enumeration type

Included by default in the core bundle, HarmonyCMS provides a base implementation to define doctrine column types that are mapped to `MyCLabs\Enum\Enum` objects.  
Enum type is fully compatible with ORM \(SQL\) and ODM \(MongoDB\) databases.

This feature is based on the [acelaya/doctrine-enum-type](https://packagist.org/packages/acelaya/doctrine-enum-type) package and use the fantastic [myclabs/php-enum](https://github.com/myclabs/php-enum) package.

## Creating a custom type

To create a custom type, you just need to create a class with some constants like:

```php
<?php
namespace App\Enum;

use MyCLabs\Enum\Enum;

class Action extends Enum
{
    public const CREATE = 'create';
    public const READ   = 'read';
    public const UPDATE = 'update';
    public const DELETE = 'delete';
}
```

## Registering custom type

CoreBundle provides 2 classes that extends `Doctrine\DBAL\Types\Type`. You can use them to easily map type names to concrete Enums.

To do that, you can register your custom enumeration type for both Doctrine ORM and ODM:

```php
<?php
use App\Enum\Action;
use Harmony\Bundle\CoreBundle\Doctrine\Type\PhpEnumType;
use Harmony\Bundle\CoreBundle\Doctrine\Type\PhpOdmEnumType;

// Doctrine ORM
PhpEnumType::registerEnumType(Action::class);
// Doctrine ODM
PhpOdmEnumType::registerEnumType(Action::class);
```

## Using custom type

The column type of the action property is the FQCN of the `Action` enum, like:

```php
<?php
namespace App\Entity;

use App\Enum\Action;
use Doctrine\ORM\Mapping as ORM;

/**
 * @ORM\Entity()
 */
class Test
{
    /**
     * @ORM\Column(type=Action::class)
     */
    protected $action;
}
```

## Customize value casting

The library assumes all the values of the enumeration are `strings`, but that might not always be the case. This library provides a way to define hooks which customize how values are cast **from** the database and **to** the database, by using the `castValueIn` and `castValueOut` static methods in the enumeration.

For example, let's imagine we have this enum:

```php
<?php
namespace App\Enum;

use MyCLabs\Enum\Enum;

class Status extends Enum
{
    public const SUCCESS = 1;
    public const ERROR   = 2;
}
```

Using the generics `PhpEnumType` or `PhpOdmEnumType` would cause an error when casting the value from the database, since it will be deserialized as a string.

In order to get it working, you have to add the `castValueIn` static method in the enum:

```php
<?php
namespace App\Enum;

use MyCLabs\Enum\Enum;

class Status extends Enum
{
    public const SUCCESS = 1;
    public const ERROR   = 2;

    public static function castValueIn($value)
    {
        return (int) $value;
    }
}
```

This method is automatically invoked before checking if the value is valid, and creating the enum instance.

The same way, a `castValueOut` method can be defined in order to modify the value before getting it persisted into the database.

```php
<?php
namespace App\Enum;

use MyCLabs\Enum\Enum;

class Gender extends Enum
{
    public const MALE   = 'male';
    public const FEMALE = 'female';

    public static function castValueOut(self $value)
    {
        return \strtolower((string) $value);
    }
}
```

These methods can also be used to customize the values. For example, if you used to have values with underscores and want to replace them by dashes, you could define these methods in your enum, in order to keep backward compatibility.

```php
<?php
// ...
public static function castValueIn($value)
{
    return \str_replace('_', '-', $value);
}

public static function castValueOut(self $value)
{
    return \str_replace('-', '_', (string) $value);
}
```

