# PHPStan

## Level

When possible setup phpstan to run at its maximum level like so.

```neon
parameters:
    level: 9
    # ...
```

### See

[PHPStan rule levels](https://phpstan.org/user-guide/rule-levels)

## Tolerance

Tolerate 0 error/warning.

## Useless docblock

Don't docblock annotate if you don't add anything to the actual php.

### 👍 Do

```php
function hello(string $name): string
{
    return 'Hello ' . $name;
}
```

```php
/**
 * @param string[] $people
 */
function congratulate(array $people): void
{
    foreach ($people as $person) {
        echo 'Congrats ' . $person;
    }
}
```

### 👎 Don't

```php
/**
 * @param string $name
 * @return string
 */
function hello(string $name): string
{
    return 'Hello ' . $name;
}
```

## PHP type hinting first, docblock second

Docblock annotation are only there to add information to php type hinting.

### 👍 Do

```php
function hello(string $name): string {
    return 'Hello ' . $name;
}
```

### 👎 Don't

```php
/**
 * @param string $name
 * @return string
 */
function hello($name): string {
    return 'Hello ' . $name;
}
```

## Docblock escape

Don't use docblock to avoid addressing issues raised by phpstan

### 👍 Do

```php
function content(string $file): string {
    return file_get_contents($file) ?: '';
}
```

### 👎 Don't

```php
// file_get_contents return string|false and not string
function content(string $file): string {
    /** @var string */
    $content = file_get_contents($file);

    return $content;
}
```
