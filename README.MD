# Php 7 upgrade tools

This repository installs a set of tools for upgrading PHP installation to PHP 7.

## Installation

Clone the repository and run ``composer install``, this will setup all the tool and configure them. This installation only works on Linux.

## Installed tools

### PHP Compatibility Coding Standard for PHP_CodeSniffer

This is a set of sniffs for PHP_CodeSniffer that checks for PHP version compatibility. It will allow you to analyse your code for compatibility with higher and lower versions of PHP.

[phpcompatibility/PHPCompatibility](https://github.com/phpcompatibility/PHPCompatibility)

### Command

In your console run ``vendor/bin/phpcs -p /path/to/code --standard=PHPCompatibility -v --report-full=report-file --extensions=php -n`` to run PHP Compatibility checker.


## Example libraries 

For very old sites, where you want some quick fixes for old the `mysql_*` and `ereg_*` functions you can include the following shims.

### PHP 7 Shim for ext/mysql

This library attempts to create a drop-in replacement for ext/mysql on PHP 7 using mysqli.

[dshafik/php7-mysql-shim](https://github.com/dshafik/php7-mysql-shim)
 bbrala/php7-ereg-shim
 
`composer require dshafik/php7-mysql-shim --dev`
 
### PHP 7 Ereg shim
    
Simple shim that can be included in old PHP 5 projects to provide ereg functionality through preg. Makes your life upgrading to PHP 7 a lot easier. 

[bbrala/php7-ereg-shim](https://github.com/bbrala/php7-ereg-shim)

`composer require bbrala/php7-ereg-shim --dev`

## Snippets

### Preg replace eval has been removed

Preg match with the [eval flag (/e) has been removed](http://php.net/manual/en/reference.pcre.pattern.modifiers.php#reference.pcre.pattern.modifiers.eval). 

#### Before
```
<?php
$html = $_POST['html'];

// uppercase headings
$html = preg_replace(
    '(<h([1-6])>(.*?)</h\1>)e',
    '"<h$1>" . strtoupper("$2") . "</h$1>"',
    $html
);
```

#### After
```
<?php
$html = $_POST['html'];

// uppercase headings
$html = preg_replace_callback(
    '(<h([1-6])>(.*?)</h\1>)',
    function ($m) {
        return "<h$m[1]>" . strtoupper($m[2]) . "</h$m[1]>";
    },
    $html
);
```

