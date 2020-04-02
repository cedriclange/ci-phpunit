phpunit

this repo has been build to solve issues #34 and #311

An easier way to use PHPUnit with [CodeIgniter](https://github.com/bcit-ci/CodeIgniter) 3.x.

* You don't have to modify CodeIgniter core files at all.
* You can write controller tests easily.
* Nothing is untestable, maybe.
* Well documented.

![Screenshot: Running tests on NetBeans 8.1](https://pbs.twimg.com/media/CUUmhxWVAAAwx3b.png)

## Requirements

* PHP 5.4.0 or later (5.6 or later is recommended)
* CodeIgniter 3.x
* PHPUnit 4.3 to 7.5 (4.8 or later is recommended)
  * If you want to use PHPUnit 8 or later, please use ci-phpunit-test [2.x](https://github.com/kenjis/ci-phpunit-test/tree/2.x).
  * If you use PHPUnit 6.0, please use ci-phpunit-test v0.14.0 or later.
  * You can download old version of `phpunit.phar` from <https://phar.phpunit.de/>.

## Optional

* NetBeans
  * Go to *Project Properties > Testing > PHPUnit*, check *Use Custom Test Suite* checkbox, and select `application/tests/_ci_phpunit_test/TestSuiteProvider.php`.

## Change Log

See [Change Log](https://github.com/kenjis/ci-phpunit-test/blob/master/application/tests/_ci_phpunit_test/ChangeLog.md).

## Folder Structure

~~~
codeigniter/
├── application/
│   └── tests/
│        ├── _ci_phpunit_test/ ... don't touch! files ci-phpunit-test uses
│        ├── Bootstrap.php     ... bootstrap file for PHPUnit
│        ├── DbTestCase.php    ... DbTestCase class
│        ├── TestCase.php      ... TestCase class
│        ├── controllers/      ... put your controller tests
│        ├── libraries/        ... put your library tests
│        ├── mocks/
│        │   └── libraries/    ... mock libraries
│        ├── models/           ... put your model tests
│        └── phpunit.xml       ... config file for PHPUnit
└── vendor/
~~~

## Installation

1. Download latest `ci-phpunit-test` from <https://github.com/kenjis/ci-phpunit-test/releases>.
2. Unzip and copy `application/tests` folder into your `application` folder in CodeIgniter project.

That's it.

### Installation via Composer

If you like Composer:

~~~
$ cd /path/to/codeigniter/
$ composer require kenjis/ci-phpunit-test --dev
~~~

And run `install.php`:

~~~
$ php vendor/kenjis/ci-phpunit-test/install.php --from-composer
~~~

* The above command always overwrites existing files.
* You must run it at CodeIgniter project root folder.
* Please remove the line `<exclude>./_ci_phpunit_test/</exclude>` in [tests/phpunit.xml](https://github.com/kenjis/ci-phpunit-test/blob/master/application/tests/phpunit.xml#L8).
* You can specify your `application` and `public` folder with option arguments, if you use custom folder paths.

~~~
$ php vendor/kenjis/ci-phpunit-test/install.php -a <application_dir> -p <public_dir>
~~~

* But some paths may be not correct, in that case, please fix them in [tests/Bootstrap.php](https://github.com/kenjis/ci-phpunit-test/blob/master/application/tests/Bootstrap.php#L96).

## Upgrading

1. Download latest `ci-phpunit-test` from <https://github.com/kenjis/ci-phpunit-test/releases>.
2. Unzip and replace `application/tests/_ci_phpunit_test` folder.
3. Read [Change Log](https://github.com/kenjis/ci-phpunit-test/blob/master/application/tests/_ci_phpunit_test/ChangeLog.md).

### Upgrading via Composer

If you like Composer:

~~~
$ cd /path/to/codeigniter/
$ composer update kenjis/ci-phpunit-test
~~~

If you're upgrading from a previous version of `ci-phpunit-test` that created
an `application/test/_ci_phpunit_test` directory and now want to directly use
`ci-phpunit-test` from Composer, you have a couple of additional steps:

1. Delete the old test library directory: `rm -rf /path/to/codeigniter/application/tests/_ci_phpunit_test`
2. Edit the `application/tests/Bootstrap.php` file.  At the bottom of the "set the main path constants"

