Google Geocoder API for Lavarel 4
======================

This package provides simple facility to make Google Geocoder API [**The Google Geocoding API**]
(https://developers.google.com/maps/documentation/geocoding/) calls to use with [**Laravel 4**](http://laravel.com/).


Installation
------------

To install edit `composer.json` and add:

```javascript
"alexpechkarev/google-geocoder": "1.*"
```

Configuration
-------------

Once installed, register Laravel service provider, in your `app/config/app.php`:

```php
'providers' => array(
	...
    'Alexpechkarev\GoogleGeocoder\GoogleGeocoderServiceProvider',
)
```

Add the facade in your `app/config/app.php`:

```php
'aliases' => array(
	...
	'Geocoder'=> 'Alexpechkarev\GoogleGeocoder\Facades\GoogleGeocoderFacade',
)
```



Publish configuration file:

```
$ php artisan config:publish alexpechkarev/google-geocoder --path vendor/alexpechkarev/google-geocoder/src/config/
```


Usage
-----

Before making calls please ensure you obtain API Key to identify your application and add this key in the configuration file.
More information on API Key please refer to [**The Google Geocoding API**](https://developers.google.com/maps/documentation/geocoding/#api_key).

```php
'applicationKey' => 'your-api-key',
```

Create an array with key=>value pairs specifying address you would like to geocode:

```php
$param = array("address"=>"76 Buckingham Palace Road London SW1W 9TQ");
```

Use following command to receive Geocoding response in json format, use xml as fist parameter for XML response.

```php
$reponse = Geocoder::geocode('json', $param);
```

To restrict your results to a specific area use component filter [***Component Filtering***](https://developers.google.com/maps/documentation/geocoding/#ComponentFiltering)
by adding it's filters to parameter array.

```php
$param = array(
                "address"=>"76 Buckingham Palace Road London SW1W 9TQ",
                "componets"=>"country:GB"
            );
```

Geocoding API supports translation of map coordinates into human-readable address 
by reverse geocoding using latitude and longitude parameters. For more details refer to [***Reverse Geocoding (Address Lookup)***]{https://developers.google.com/maps/documentation/geocoding/#ReverseGeocoding}
To make reverse geocoding request use following:

```php
$param = array("latlng"=>"40.714224,-73.961452");
$reponse = Geocoder::geocode('json', $param);
```

All request will return `string` result. For Response example, Status Codes, Error Messages and Results please refer to [***Geocoding Responses***](https://developers.google.com/maps/documentation/geocoding/#GeocodingResponses)



Support
-------

[Please open an issue on GitHub](https://github.com/alexpechkarev/google-geocoder/issues)


License
-------

GeocoderLaravel is released under the MIT License. See the bundled
[LICENSE](https://github.com/alexpechkarev/google-geocoder/blob/master/LICENSE)
file for details.