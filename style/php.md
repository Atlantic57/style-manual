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

* A file *SHOULD* declare new symbols (classes, functions, constants, etc.) and cause no other side effects, or it SHOULD execute logic with side effects, but SHOULD NOT do both.
* The phrase "side effects" means execution of logic not directly related to declaring classes, functions, constants, etc., merely from including the file.
* "Side effects" include but are not limited to: generating output, explicit use of require or include, connecting to external services, modifying ini settings, emitting errors or exceptions, modifying global or static variables, reading from or writing to a file, and so on.

_[Examples can be seen here](http://www.php-fig.org/psr/psr-1/#2-3-side-effects "Side Effect Examples")._

### 3. Namespace and Class Names

* Namespaces and classes *MUST* follow the latest "autoloading" PSR - [PSR-4](http://www.php-fig.org/psr/psr-4/ "PSR-4 Autoloading Standard"). _This section is debatable. the official PSR-1 spec recommends using PSR-0 for PHP 5.2 and below and PSR-4 for PHP 5.3 and above. I (Tommy) can't imagine a scenario where we would need to use PSR-0. Can anyone else think of a use case?_
* This means each class is in a file by itself, and is in a namespace of at least one level: a top-level vendor name.
* Class names *MUST* be declared in `StudlyCaps`.
* Code *MUST* use formal namespaces.

_For example:_
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

Class constants *MUST* be declared in all upper case with underscore separators.

_For example:_
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

_TODO: We need to decide whether we want to use `$StudlyCaps`, `$camelCase`, or `$under_score` for property names since none of the PSR's make a reccomendation regarding this. I (Tommy) think we should avoid `$StudlyCaps` so those are reserved for classes and use either `$camelCase` or `$under_score`._

#### 4.3. Methods

Method names *MUST* be declared in `camelCase()`.

## PHP Coding Style Guide
_This coding style guide is adapted from [PSR-2](http://www.php-fig.org/psr/psr-2/ "PSR-2 PHP Coding Style Guide"). It is assumed that the coding standards outlined above will be followed._

### 1. Overview

* Code *MUST* use 4 spaces for indenting, not tabs.
* There *MUST* NOT be a hard limit on line length; the soft limit *MUST* be 120 characters; lines *SHOULD* be 80 characters or less.
* There *MUST* be one blank line after the namespace declaration, and there *MUST* be one blank line after the block of use declarations.
* Opening braces for classes *MUST* go on the next line, and closing braces *MUST* go on the next line after the body.
* Opening braces for methods *MUST* go on the next line, and closing braces *MUST* go on the next line after the body.
* Visibility *MUST* be declared on all properties and methods; abstract and final *MUST* be declared before the visibility; static *MUST* be declared after the visibility.
* Control structure keywords *MUST* have one space after them; method and function calls *MUST NOT*.
* Opening braces for control structures *MUST* go on the same line, and closing braces *MUST* go on the next line after the body.
* Opening parentheses for control structures *MUST NOT* have a space after them, and closing parentheses for control structures *MUST NOT* have a space before.

#### 1.1. Example
_This example encompasses some of the rules below as a quick overview:_

```
<?php
namespace Vendor\Package;

use FooInterface;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class Foo extends Bar implements FooInterface
{
    public function sampleFunction($a, $b = null)
    {
        if ($a === $b) {
            bar();
        } elseif ($a > $b) {
            $foo->bar($arg1);
        } else {
            BazClass::bar($arg2, $arg3);
        }
    }

    final public static function bar()
    {
        // method body
    }
}
```

### 2. General

#### 2.1. Files

* All PHP files *MUST* use the Unix LF (linefeed) line ending.
* All PHP files *MUST* end with a single blank line.
* The closing `?>` tag *MUST* be omitted from files containing only PHP.

#### 2.2. Lines

* There *MUST NOT* be a hard limit on line length.
* The soft limit on line length *MUST* be 120 characters; automated style checkers *MUST* `warn` but *MUST NOT* `error` at the soft limit.
* Lines *SHOULD NOT* be longer than 80 characters; lines longer than that *SHOULD* be split into multiple subsequent lines of no more than 80 characters each.
* There *MUST NOT* be trailing whitespace at the end of non-blank lines.
* Blank lines *MAY* be added to improve readability and to indicate related blocks of code.
* There *MUST NOT* be more than one statement per line.

#### 2.3. Indenting

Code *MUST* use an indent of 4 spaces, and *MUST NOT* use tabs for indenting.

_Note: Using only spaces, and not mixing spaces with tabs, helps to avoid problems with diffs, patches, history, and annotations. The use of spaces also makes it easy to insert fine-grained sub-indentation for inter-line alignment._

#### 2.4. Keywords and True/False/Null

* PHP [keywords]('http://php.net/manual/en/reserved.keywords.php') *MUST* be in lower case.
* The PHP constants `true`, `false`, and `null` *MUST* be in lower case.

### 3. Namespace and Use Declarations

* When present, there *MUST* be one blank line after the namespace declaration.
* When present, all use declarations *MUST* go after the namespace declaration.
* There *MUST* be one use keyword per declaration.
* There *MUST* be one blank line after the use block.

_For example:_
```
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

// ... additional PHP code ...
```

### 4. Classes, Properties, and Methods
_The term "class" refers to all classes, interfaces, and traits._

#### 4.1. Extends and Implements

* The `extends` and `implements` keywords *MUST* be declared on the same line as the class name.
* The opening brace for the class *MUST* go on its own line; the closing brace for the class *MUST* go on the next line after the body.

_For example:_
```
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess, \Countable
{
    // constants, properties, methods
}
```

* Lists of `implements` *MAY* be split across multiple lines, where each subsequent line is indented once. When doing so, the first item in the list *MUST* be on the next line, and there *MUST* be only one interface per line.

_For example:_
```
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // constants, properties, methods
}
```

#### 4.2. Properties

* Visibility *MUST* be declared on all properties.
* The var keyword *MUST NOT* be used to declare a property.
* There *MUST NOT* be more than one property declared per statement.
* Property names *SHOULD NOT* be prefixed with a single underscore to indicate protected or private visibility.

_For example:_
```
<?php
namespace Vendor\Package;

class ClassName
{
    public $foo = null;
}
```

#### 4.3. Methods

* Visibility *MUST* be declared on all methods.

* Method names *SHOULD NOT* be prefixed with a single underscore to indicate protected or private visibility.

* Method names *MUST NOT* be declared with a space after the method name. The opening brace *MUST* go on its own line, and the closing brace *MUST* go on the next line following the body. There *MUST NOT* be a space after the opening parenthesis, and there *MUST NOT* be a space before the closing parenthesis.

_For example see the following. Note the placement of parentheses, commas, spaces, and braces:_
```
<?php
namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```

#### 4.4. Method Arguments

* In the argument list, there *MUST NOT* be a space before each comma, and there *MUST* be one space after each comma.
* Method arguments with default values *MUST* go at the end of the argument list.

_For example:_
```
<?php
namespace Vendor\Package;

class ClassName
{
    public function foo($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```

* Argument lists *MAY* be split across multiple lines, where each subsequent line is indented once. When doing so, the first item in the list *MUST* be on the next line, and there *MUST* be only one argument per line.
* When the argument list is split across multiple lines, the closing parenthesis and opening brace *MUST* be placed together on their own line with one space between them.

_For example:_
```
<?php
namespace Vendor\Package;

class ClassName
{
    public function aVeryLongMethodName(
        ClassTypeHint $arg1,
        &$arg2,
        array $arg3 = []
    ) {
        // method body
    }
}
```

#### 4.5. Abstract, Final, and Static

* When present, the `abstract` and `final` declarations *MUST* precede the visibility declaration.
* When present, the `static` declaration *MUST* come after the visibility declaration.

_For example:_
```
<?php
namespace Vendor\Package;

abstract class ClassName
{
    protected static $foo;

    abstract protected function zim();

    final public static function bar()
    {
        // method body
    }
}
```
