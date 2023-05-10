Updating table migration column to tinyInteger will throw an error since laravel doesn't support tinyInteger in `doctrine/dbal` package.

Laravel provides means to solve this problem, below is complete solution for MySQL for both `TINYINT` and `TINYINT UNSIGNED`. I'm using Laravel 10 and PHP 8.1 here, probably works for other versions.

`app/Doctrine/TinyInteger.php`:
```php
<?php

namespace App\Doctrine;

use Doctrine\DBAL\ParameterType;
use Doctrine\DBAL\Platforms\AbstractPlatform;
use Doctrine\DBAL\Types\Type;

class TinyInteger extends Type
{
    /**
     * The name of the custom type.
     */
    public const NAME = 'tinyinteger';

    /**
     * {@inheritdoc}
     */
    public function convertToPHPValue($value, AbstractPlatform $platform)
    {
        return $value === null ? null : (int)$value;
    }

    /**
     * {@inheritdoc}
     */
    public function getSQLDeclaration(array $column, AbstractPlatform $platform): string
    {
        $unsigned = !empty($column['unsigned']) ? ' UNSIGNED' : '';
        $autoincrement = !empty($column['autoincrement']) ? ' AUTO_INCREMENT' : '';

        return 'TINYINT' . $unsigned . $autoincrement;
    }

    /**
     * {@inheritdoc}
     */
    public function getName(): string
    {
        return static::NAME;
    }

    /**
     * {@inheritdoc}
     */
    public function getBindingType(): int
    {
        return ParameterType::INTEGER;
    }
}
```

`config/database.php`:
```php
<?php

use App\Doctrine\TinyInteger;

return [
    // ...

    'dbal' => [
        'types' => [
            TinyInteger::NAME => TinyInteger::class,
        ],
    ],

    // ...
];
```

That is enough, now your Laravel project knows TINYINT, no special code needed in migrations in contradistinction to other solutions above.  
This approach is tested and should be good enough for single type of database. You may rewrite method `getSQLDeclaration` for your database of choice. If you want to support multiple types of databases, you will need to refactor `getSQLDeclaration`: it is better to move all real logic to separate Grammar classes (MysqlGrammar, PostgresqlGrammar, etc.) and choose appropriate one using condition `$platform instanceof`.

Inspired by `Doctrine\DBAL\Types\SmallIntType` and Laravel documentation [https://laravel.com/docs/10.x/migrations#modifying-columns-on-sqlite](https://laravel.com/docs/10.x/migrations#modifying-columns-on-sqlite)

Hope it helps to someone.