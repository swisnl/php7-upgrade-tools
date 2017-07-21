# Php 7 upgrade tools

This repository installs a set of tools for upgrading PHP installation to PHP 7.

## Installation

Clone the repository and run ``composer install``, this will setup all the tool and configure them. This installation only works on Linux.

## Installed tools

### PHP Compatibility Coding Standard for PHP_CodeSniffer

This is a set of sniffs for PHP_CodeSniffer that checks for PHP version compatibility. It will allow you to analyse your code for compatibility with higher and lower versions of PHP.

[wimg/PHPCompatibility](https://github.com/wimg/PHPCompatibility)

### PHP 7 Compatibility Checker (php7cc)

php7cc is a command line tool designed to make migration from PHP 5.3-5.6 to PHP 7 easier. It searches for potentially troublesome statements in existing code and generates reports containing file names, line numbers and short problem descriptions. It does not automatically fix code to work with the new PHP version.

[sstalle/php7cc](https://github.com/sstalle/php7cc)

### Command

In your console run ``./vendor/bin/php7cc /path/to/your/code`` to run PHP Compatibility checker.


## Example libraries 

For very old sites, where you want some quick fixes for old the `mysql_*` and `ereg_*` functions you can include the following shims.

### PHP 7 Shim for ext/mysql

This library attempts to create a drop-in replacement for ext/mysql on PHP 7 using mysqli.

[dshafik/php7-mysql-shim](https://github.com/dshafik/php7-mysql-shim)
 bbrala/php7-ereg-shim
### PHP 7 Ereg shim
    
Simple shim that can be included in old PHP 5 projects to provide ereg functionality through preg. Makes your life upgrading to PHP 7 a lot easier. 

[bbrala/php7-ereg-shim](https://github.com/bbrala/php7-ereg-shim)

composer require dshafik/php7-mysql-shim --dev
composer require bbrala/php7-ereg-shim --dev 