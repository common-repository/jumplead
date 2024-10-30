# Jumplead WordPress Plugin

## Development Environment

* Docker + Docker Compose
* In terminal, from the trunk folder: ```docker-compose up -d```.
* [http://localhost:8080](http://localhost:8080).
* Jumplead will need to be activated via Plugins section.
* For debugging, add ```define('WP_DEBUG', true);``` to wp-config.php.
* To test upcoming WP releases
    * Install "WordPress Beta Tester" plugin,
    * Select "nightly" in Tools > Beta Testing,
    * Head to [/wp-admin/update-core.php](http://localhost:8080/wp-admin/update-core.php)
    * Install latest version

---

## How To Tag

* Update Version References
    * readme.txt: `Stable tag: ~TAG~`
    * jumplead.php: `Version: ~TAG~` and `define( 'JUMPLEAD_VERSION', '~TAG~' );`
* `svn copy trunk tags/~TAG~`
* `svn commit -m "Tagged ~TAG~"`

---

## Coding Standards

We use THREE different coding standards checkers.

### PHP Compatibility

[https://github.com/wimg/PHPCompatibility](https://github.com/wimg/PHPCompatibility)

Supports PHPCS <2.

* Install: ```composer install```
* Run ```sh codingstandards.sh```
* Fix: Manual (until it supports PHPCS 2+)

### WordPress Coding Standards

[https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards](https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards)

Supports PHPCS 2+ only.

* Outside of this project's folder, Install:

```
composer create-project wp-coding-standards/wpcs:dev-master --no-dev;
phpcs --config-set installed_paths <PATH TO WPCS>;
```

* Run ```sh codingstandards.sh```
* Fix: ``` phpcbf ./ --standard=WordPress```

### Short Array Syntax Checker

* Install: Nothing. Just a ```pcregrep``` command
* Run ```sh codingstandards.sh```
* Fix: Manual

---

## Integrations

### JetPack

* Add ```define('JETPACK_DEV_DEBUG', true);``` to wp-config.php

#### Sample Form

    [contact-form]
        [contact-field label='First Name' type='name' required='1'/]
        [contact-field label='Last Name' type='text'/]
        [contact-field label='Email' type='email' required='1'/]
        [contact-field label='Company' type='text'/]
    [/contact-form]

### Contact Form 7

#### Sample Form

    <p>First Name (required)<br />[text* first-name] </p>
    <p>Last Name (required)<br />[text* last-name]</p>
    <p>Your Email (required<br />[email* your-email]</p>
    <p>Company (required)<br />[text* company]</p>
    <p>[submit "Send"]</p>

### Formidable

* Create a form inside WordPress admin.
