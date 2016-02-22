# AMS PHP Style Guide

## PHP Coding Standards
_These coding standards are adapted from [PSR-1](http://www.php-fig.org/psr/psr-1/ "PSR-1 Coding Standard")_

### 1. Overview

* Files *MUST* use only `<?php` and `<?=` tags.
* Files *MUST* use only UTF-8 without BOM for PHP code.
* Files *SHOULD* either declare symbols (classes, functions, constants, etc.) or cause side-effects (e.g. generate output, change .ini settings, etc.) but *SHOULD NOT* do both.
* Namespaces and classes *MUST* follow the latest "autoloading" PSR - [PSR-4](http://www.php-fig.org/psr/psr-4/ "PSR-4 Autoloading Standard").
* Class names *MUST* be declared in `StudlyCaps`.
* Class constants *MUST* be declared in all upper case with underscore separators.
* Method names *MUST* be declared in `camelCase`.

### 2. Files

#### 2.1. PHP Tags

PHP code *MUST* use the long `<?php ?>` tags or the short-echo `<?= ?>` tags; it MUST NOT use the other tag variations.

#### 2.2 Character Encoding

PHP code *MUST* use only UTF-8 without BOM.

#### 2.3. Side Effects

A file *SHOULD* declare new symbols (classes, functions, constants, etc.) and cause no other side effects, or it SHOULD execute logic with side effects, but SHOULD NOT do both.

The phrase "side effects" means execution of logic not directly related to declaring classes, functions, constants, etc., merely from including the file.

"Side effects" include but are not limited to: generating output, explicit use of require or include, connecting to external services, modifying ini settings, emitting errors or exceptions, modifying global or static variables, reading from or writing to a file, and so on.

[Examples can be seen here](http://www.php-fig.org/psr/psr-1/#2-3-side-effects "Side Effect Examples").

### 3. Namespace and Class Names

Namespaces and classes *MUST* follow the latest "autoloading" PSR - [PSR-4](http://www.php-fig.org/psr/psr-4/ "PSR-4 Autoloading Standard"). _This section is debatable. the official PSR-1 spec recommends using PSR-0 for PHP 5.2 and below and PSR-4 for PHP 5.3 and above. I (Tommy) can't imagine a scenario where we would need to use PSR-0. Can anyone else think of a use case?_

This means each class is in a file by itself, and is in a namespace of at least one level: a top-level vendor name.

Class names *MUST* be declared in `StudlyCaps`.

Code *MUST* use formal namespaces.

For example:

```
<?php
namespace Vendor\Model;

class Foo
{
}
```

### 4 Class Constants, Properties and Methods

_The term "class" refers to all classes, interfaces, and traits._

#### 4.1. Constants

Class constants *MUST* be declared in all upper case with underscore separators. For example:

```
<?php
namespace Vendor\Model;

class Foo
{
    const VERSION = '1.0';
    const DATE_APPROVED = '2012-06-01';
}
```

#### 4.2. Properties

_TODO: We need to decide whether we want to use `$StudlyCaps`, `$camelCase`, or `$under_score` for property names sense none of the PSR's make a reccomendation regarding this. I (Tommy) think we should avoid `$StudlyCaps` so those are reserved for classes and use either `$camelCase` or `$under_score`._

#### 4.3. Methods

Method names *MUST* be declared in `camelCase()`.