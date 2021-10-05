# PHP

Code style must follow [PSR-1](http://www.php-fig.org/psr/psr-1/), [PSR-2](http://www.php-fig.org/psr/psr-2/) and [PSR-12](https://www.php-fig.org/psr/psr-12/). Generally speaking, everything string-like that's not public-facing should use camelCase. Detailed examples on these are spread throughout the guide in their relevant sections.

## Resources

- [PHP Programming Language Tutorial - Full Course](https://www.youtube.com/watch?v=OK_JCtrrv-c)
- [Top 12 VScode Extensions for PHP](https://www.youtube.com/watch?v=v9dWFbiir9Q)

## Recommended Tools

- [Visual Studio Code](https://visualstudio.microsoft.com/)
- [PHPStorm](https://www.jetbrains.com/phpstorm/)

## General Concepts

- The first line of all .php files should be exactly "<?php"
- Never use the closing PHP tag (?>)
- Never use PHP short tags
- All files must only use UTF-8, without BOM
- Always use UTC timezone to store date and time
- Every .php library file should contain one class exactly
- Every .php library file should be side effect free
- Singular words (e.g. item, stylesheet, user) should be used throughout files and code instead of plurals
- Avoid Hungarian Notation, where file/variable names that indicate their type
- Use camelCase for variable naming
- Never use global variables
- Properties should always be declared
- Variables should always be declared at the top of the block they are used in
- Avoid using final keyword unless necessary
- Avoid calling functions in global namespace
- Indentation and whitespace
- Use the tab character for indentation
- Avoid "double-indenting" blocks of code where no indentation is necessary for readability
- Do not leave whitespace at the end of lines
- Be as strict as is sensible to enforce 80 character lines
- Limit to three levels of indentation within functions

## Brackets and braces

- Opening braces should always be placed at the end of the line
- Closing braces should always be placed at the start of their own line
- One level of indentation should be applied within, and only within, the braces
- Conditionals within brackets should not gain extra indentation when breaking onto separate lines
- Never leave conditional statements unbraced or unindented

## Spaces

- No extra space should be placed after a control structure keyword or function name
- Opening brackets should not have a space after, closing brackets should not hace a space before
- Commas separating variable lists should have a space or newline after, no whitespace before
- A space should surround binary and ternary, but not unary operators
- A space should surround all type operators

### Void spaces

Statements should have to breathe. In general always add blank lines between statements, unless they're a sequence of single-line equivalent operations. This isn't something enforceable, it's a matter of what looks best in its context.

```php
// Good
public function getPage($url)
{
    $page = $this->pages()->where('slug', $url)->first();

    if (! $page) {
        return null;
    }

    if ($page['private'] && ! Auth::check()) {
        return null;
    }

    return $page;
}

// Bad: Everything's cramped together.
public function getPage($url)
{
    $page = $this->pages()->where('slug', $url)->first();
    if (! $page) {
        return null;
    }
    if ($page['private'] && ! Auth::check()) {
        return null;
    }
    return $page;
}
```

```php
// Good: A sequence of single-line equivalent operations.
public function up()
{
    Schema::create('users', function (Blueprint $table) {
        $table->increments('id');
        $table->string('name');
        $table->string('email')->unique();
        $table->string('password');
        $table->rememberToken();
        $table->timestamps();
    });
}
```

Don't add any extra empty lines between `{}` brackets.

```php
// Good
if ($foo) {
    $this->foo = $foo;
}

// Bad
if ($foo) {

    $this->foo = $foo;

}
```
## Directories, files and namespaces

- Directories and files must either be namespace-mapped or web-mapped
- Namespaces must map to file paths, as per PSR-4
- Files and directories should be lowercase-hyphenated where not namespace-mapped
- Namespace-mapped files and directories must use `UpperCamelCase`
- Web mapped files and directories must use `lowercase-hyphenated-words`

## Class defaults

By default, we don't use `final`. For our open source stuff, we assume that all our users know they are responsible for writing tests for any overwritten behaviour.

- The term "class" refers to all classes, interfaces, and traits
- A class should only ever be autoloaded - never use `require` or `include`
- Constants should only be declared on a class
- Constants should use `UPPERCASE_UNDERSCORED`
- Properties should use `$camelCase`
- Methods should use `camelCase()`
- Classes should have all or no static members
- All parameters should define their type where possible
- All methods should define their return type where possible
- Methods should avoid becoming longer than 20-50 lines

## Void return types

If a method return nothing, it should be indicated with `void`.
This makes it more clear to the users of your code what your intention was when writing it.

### Databases

- Queries should be organised into a Query Collection Hierarchy
- Tables should use `PascalCase`
- Related tables should use an underscore to indicate their hierarchy
- Columns should use `camelCase`
- Primary keys should be called `id`
- Column names should be treated exactly as object properties are
- Foreign key column names do not need special identification
- Foreign key constraint names should reference both tables and columns uniquely

## Comments

- For inline comments, double-slash comments (`//`) should be used
- Inline comments should have no indentation, starting from column 1
- Inline comments can span multiple lines, prefixed with the double-slash
- Block comments should only be used to provide class and method documentation in the form of doc blocks
- Comments, along with docblocks, should be sparse and punchy to avoid stale documentation

Comments should be avoided as much as possible by writing expressive code. If you do need to use a comment, format it like this:

```php
// There should be a space before a single line comment.

/*
 * If you need to explain a lot you can use a comment block. Notice the
 * single * on the first line. Comment blocks don't need to be three
 * lines long or three characters shorter than the previous line.
 */
```

## Data structures

- Data structures representing collections should be array-accessible and/or iterable
- Data structures representing individual items should use getter functions
- Associative arrays should only be used for simple key-value-pairs
- Move associative arrays to an object's getter/setter storage where possible
- Static classes should only be used when truly stateless
- Private methods should be preferred over anonymous functions where appropriate
- Anonymous functions should never exceed 5-10 lines

## Typed properties

You should type a property whenever possible. Don't use a docblock.

```php
// good
class Foo
{
    public string $bar;
}

// bad
class Foo
{
    /** @var string */
    public $bar;
}
```

## Docblocks

- Use full stops to end full sentences
- Don't use full stops to end fragmented sentences
- Choose either full sentences or fragments in lists (not both)

Don't use docblocks for methods that can be fully type hinted (unless you need a description).

Only add a description when it provides more context than the method signature itself. Use full sentences for descriptions, including a period at the end.

```php
// Good
class Url
{
    public static function fromString(string $url): Url
    {
        // ...
    }
}

// Bad: The description is redundant, and the method is fully type-hinted.
class Url
{
    /**
     * Create a url from a string.
     *
     * @param string $url
     *
     * @return \Spatie\Url\Url
     */
    public static function fromString(string $url): Url
    {
        // ...
    }
}
```

Always use fully qualified class names in docblocks.

```php
// Good

/**
 * @param string $url
 *
 * @return \Spatie\Url\Url
 */

// Bad

/**
 * @param string $foo
 *
 * @return Url
 */
```

Docblocks for class variables are required, as there's currently no other way to typehint these.

```php
// Good

class Foo
{
    /** @var \Spatie\Url\Url */
    private $url;

    /** @var string */
    private $name;
}

// Bad

class Foo
{
    private $url;
    private $name;
}
```

When possible, docblocks should be written on one line.

```php
// Good

/** @var string */
/** @test */

// Bad

/**
 * @test
 */
```

If a variable has multiple types, the most common occurring type should be first.

```php
// Good

/** @var \Spatie\Goo\Bar|null */

// Bad

/** @var null|\Spatie\Goo\Bar */
```

## Strings

When possible prefer string interpolation above `sprintf` and the `.` operator.

```php
// Good
$greeting = "Hi, I am {$name}.";
```

```php
// Bad
$greeting = 'Hi, I am ' . $name . '.';
```


## Ternary operators

Every portion of a ternary expression should be on its own line unless it's a really short expression.

```php
// Good
$result = $object instanceof Model
    ? $object->name
    : 'A default value';

$name = $isFoo ? 'foo' : 'bar';

// Bad
$result = $object instanceof Model ?
    $object->name :
   'A default value';
```

## If statements

### Bracket position

Always use curly brackets.

```php
// Good
if ($condition) {
   ...
}

// Bad
if ($condition) ...
```

### Happy path

Generally a function should have its unhappy path first and its happy path last. In most cases this will cause the happy path being in an unindented part of the function which makes it more readable.

```php
// Good

if (! $goodCondition) {
  throw new Exception;
}

// do work
```


```php
// Bad

if ($goodCondition) {
 // do work
}

throw new Exception;
```

### Avoid else

In general, `else` should be avoided because it makes code less readable. In most cases it can be refactored using early returns. This will also cause the happy path to go last, which is desirable.

```php
// Good

if (! $conditionBA) {
   // conditionB A failed
   
   return;
}

if (! $conditionB) {
   // conditionB A passed, B failed
   
   return;
}

// condition A and B passed
```

```php
// Bad

if ($conditionA) {
   if ($conditionB) {
      // condition A and B passed
   }
   else {
     // conditionB A passed, B failed
   }
}
else {
   // conditionB A failed
}
```


### Compound ifs

In general, separate `if` statements should be preferred over a compound condition. This makes debugging code easier.


```php
// Good
if (! $conditionA) {
   return;
}

if (! $conditionB) {
   return;
}

if (! $conditionC) {
   return;
}

// do stuff
```

```php
// bad
if ($conditionA && $conditionB && $conditionC) {
  // do stuff
}
```

