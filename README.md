# Hostfact API 3.0 for Laravel

[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fhyperized%2Fhostfact.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Fhyperized%2Fhostfact?ref=badge_shield)

Official documentation:
-----------------------

* [Hostfact API documentation](https://www.hostfact.nl/developer/api/)

Installation
------------

Install using composer:

```bash
composer require hyperized/hostfact
```

This package supports Package Auto-Discovery (Laravel 5.5+) so it doesn't require you to manually add the
ServiceProvider and alias.

If you are using a lower version of Laravel or not using Auto-Discovery you can add the Hostfact Service Provider to
the `config/app.php` file

```php
Hyperized\Hostfact\HostfactServiceProvider::class,
```

Register an alias for Hostfact, also in `config/app.php`:

```php
'Hostfact'    => Hyperized\Hostfact\HostfactServiceProvider::class,
```

Now publish the Hostfact package into your installation:

```bash
php artisan vendor:publish --provider="Hyperized\Hostfact\HostfactServiceProvider" --tag="config"
```

This should give you a message
like: `Copied File [/vendor/hyperized/hostfact/src/config/Hostfact.php] To [/config/Hostfact.php]`

It's possible to edit your configuration variables in the `config/Hostfact.php` file or you can use the `HOSTFACT_URL`
and `HOSTFACT_KEY` environment variables to store sensitive information in the `.env` file

```php
// config/Hostfact.php
'api_v2_url'		=> env('HOSTFACT_URL', 'https://yoursite.tld/Pro/apiv2/api.php'),
'api_v2_key'		=> env('HOSTFACT_KEY', 'token'),
'api_v2_timeout'	=> env('HOSTFACT_TIMEOUT', 20),

// .env/.env.example
HOSTFACT_URL=https://yoursite.tld/Pro/apiv2/api.php
HOSTFACT_KEY=token
HOSTFACT_TIMEOUT=20
```

Functionality
---------

When writing code for this Hostfact package, consider that this package written as a basic interface.

This package will do the following:

* Provide an easy way to communicate with Hostfact API controllers;
* Document the available API controller endpoints with methods;
* Transport layer (HTTP/HTTPS) error catching;
* Basic error parsing;

This package does not:

* Parameter / input validation;
* Output validation;

You will need to consult the [Hostfact API documentation](https://www.hostfact.nl/developer/api/) to understand the
acceptable input and output for each of the API controllers.

Examples
--------

Example code:

```php
use \Hyperized\Hostfact\Api\Controllers\Product;

$products = Product::new()
                ->list([
                    'searchfor' => 'invoice'
                ]);
```

## License

[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fhyperized%2Fhostfact.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Fhyperized%2Fhostfact?ref=badge_large)