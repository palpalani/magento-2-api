# Magento2 rest api

[![Latest Version on Packagist](https://img.shields.io/packagist/v/palpalani/magento2-rest-api-client.svg?style=flat-square)](https://packagist.org/packages/palpalani/magento2-rest-api-client)
[![GitHub Code Style Action Status](https://img.shields.io/github/workflow/status/palpalani/magento2-rest-api-client/Check%20&%20fix%20styling?label=code%20style)](https://github.com/palpalani/magento2-rest-api-client/actions?query=workflow%3A"Check+%26+fix+styling"+branch%3Amain)
[![Total Downloads](https://img.shields.io/packagist/dt/palpalani/magento2-rest-api-client.svg?style=flat-square)](https://packagist.org/packages/palpalani/magento2-rest-api-client)

This is a simple PHP SDK lib to easily create Rest API.

## Installation

You can install the package via composer:

```bash
composer require palpalani/magento2-rest-api-client
```

## Example usage

```php
<?php
require __DIR__ . '/vendor/autoload.php';

$service = new \Experius\Magento2ApiClient\Service\RestApi();
$service->setUsername('username');
$service->setPassword('password');
$service->setUrl('https://www.example.com/index.php/rest/%storecode/V1/');

// OPTIONAL > default = all
$service->setStoreCode('default');

$service->init();
```

### Create product

```php
$data = json_decode('
{
    "product": {
        "custom_attributes": [
                    {
                "attribute_code": "url_key",
                "value": "experius-example-product-new"
            }
        ],
        "name": "Experius Example Product",
        "weight": 1.2,
        "visibility": 4,
        "extension_attributes": {
            "website_ids": [
                "1"
            ],
            "stock_item": {
                "is_in_stock": true
            }
        },
        "sku": "experius-example-product",
        "status": 1,
        "type_id": "simple",
        "attribute_set_id": "4",
        "price": 10
    }
}');
$result = $service->call('products', $data, 'POST');
var_dump($result);
```

### Update product

```php
$data = json_decode('
{
    "product": {
        "custom_attributes": [
                    {
                "attribute_code": "url_key",
                "value": "experius-example-product-new"
            }
        ],
        "name": "Experius Example Product",
        "weight": 1.2,
        "visibility": 4,
        "extension_attributes": {
            "website_ids": [
                "1"
            ],
            "stock_item": {
                "is_in_stock": true
            }
        },
        "sku": "experius-example-product",
        "status": 1,
        "type_id": "simple",
        "attribute_set_id": "4",
        "price": 10
    }
}');
$result = $service->call('products/experius-example-product', $data, 'PUT');
var_dump($result);
```

### Retrieve product

```php
$result = $service->call('products/experius-example-product');
var_dump($result);

$dataArray = [
    'searchCriteria' => [
        'pageSize' => 10
    ]
];

$result = $service->call('products', $dataArray);
var_dump($result);
```

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Contributing

Please see [CONTRIBUTING](.github/CONTRIBUTING.md) for details.

## Security Vulnerabilities

Please review [our security policy](../../security/policy) on how to report security vulnerabilities.

## Credits

- [palPalani](https://github.com/palpalani)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
