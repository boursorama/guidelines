# PHP

## Assertion

Use assertions as safe guards. They are not executed in production so they don't have any side effects and are taken into account by phpstan.

```php
assert(isset($response['name']), 'missing name in response');
```

### 👎 Don't

Use assertions to do business logic.

```php
assert($balance > 0, 'can\'t make cash transfer with negative balance');
```

### See

[php.net assert](https://www.php.net/manual/en/function.assert.php)

## Nested arrays

Avoid putting everything in nested arrays. You will have to do a lot of type checking at runtime in order to be sure of what data you are manipulating. If forced to use nested arrays (`json_decode`), use [Trunk](https://github.com/giann/trunk).

### 👍 Do

```php
class Person {
    public function __construct(public string $name) {}
}

$person = new Person('joe');
```

```php
$data = new Trunk(json_decode($json, true) ?: []);

$name = $data['person']['name']->stringValue();
```

### 👎 Don't

```php
$person = [
    'name' => 'Joe'
];
```

```php
$data = json_decode($json, true);

$name = $data['person']['name'];
```

## Strict typing

Put this at the start of any php script:

```php
<?php

declare(strict_types=1);
```

It will ensure that a php doesn't coerce variable of the wrong type into the expected one.

```php
<?php

declare(strict_types=1);

function hello(string $name): void
{
    echo 'Hello ' . $name;
}

hello(12); // TypeError: hello(): Argument #1 ($name) must be of type string, int given on line 8
```

### See

[php.net Strict typing](https://www.php.net/manual/en/language.types.declarations.php#language.types.declarations.strict)
