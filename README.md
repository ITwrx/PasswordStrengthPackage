PasswordStrength Package
================
[![Build Status](https://travis-ci.org/schuppo/PasswordStrengthPackage.png?branch=1.x)](https://travis-ci.org/schuppo/PasswordStrengthPackage)
[![Total Downloads](https://poser.pugx.org/schuppo/password-strength/downloads)](https://packagist.org/packages/schuppo/password-strength)
[![License](https://poser.pugx.org/schuppo/password-strength/license)](https://packagist.org/packages/schuppo/password-strength)

**[not known working until this message is gone]**

This package provides a validator that ensures strong passwords in Laravel 6 applications. It is influenced  a lot by [PasswordStrengthBundle for Symfony 2](https://github.com/jbafford/PasswordStrengthBundle).

It is out now for a while and since there were no complaints it very likely fulfills its purpose.

The provided validations include:

- check if input contains alphabetic characters
- check if input contains numeric characters
- check if input contains mixed case characters
- check if input contains symbols

# Documentation

## Installation

### Get the package

This package can be installed via Composer by adding the following to your `composer.json` file:

```
    "require": {
        "itwrx/password-strength": "dev-L6",
    }
```
under the scripts section:

```
"repositories": [
        {
            "type": "vcs",
            "url": "https://github.com/ITwrx/PasswordStrengthPackage.git"
        }
    ]
```

You must then run the following command:

```
    composer update
```


**Caution**

I recently recognized a small conflict in the usage of this package in combination with [unique-with](https://github.com/felixkiss/uniquewith-validator): One runs into problems when adding the ```PasswordStrengthServiceProvider``` **after** ```UniqueWithValidatorServiceProvider``` to the providers array, the  rules of this package stay unknown to the Laravel ```Validator```.

The problem is easy to fix though: Just add the service provider of this package in front of the service provider of *unique-with*. In that order both packages work fine.

## Usage
Now Laravel's native `Validator` is extended by four rules:

- case_diff
- numbers
- letters
- symbols

### Example
You can apply these rules as described in the [validation section on Laravel's website](http://laravel.com/docs/validation)

```php
$v = Validator::make(array(
    'password' => '12345QWERTqwert@',
    'password' => 'case_diff|numbers|letters|symbols'
));
$v->passes();   // returns true;
```

Notice that you can validate any value with the new rules. The only reason why this package is called "Password Strength Package" is that it describes its foremost purpose.

# History

This is just a fork with very minor alterations for Laravel version compat. Please see upstream for history info.

# License

This package is under the MIT license. See the complete license:

- [LICENSE](https://github.com/schuppo/PasswordStrengthPackage/LICENSE)


## Reporting Issues or Feature Requests

Issues and feature requests are tracked on [GitHub](https://github.com/schuppo/PasswordStrengthPackage/issues).
