# iploka
A PHP wrapper for using Iploka [API](https://iploka.com/)

#### Install via `composer`:
```sh
composer require ab/iploka
```

#### Basic usage

Get full data as the [Location](https://github.com/GitHubHubus/ipstack-client/blob/master/src/OK/Ipstack/Entity/Location.php) object:
```php
$client = new AB\Iploka\Client('api_key');
$location = $client->get('134.201.250.155');
var_dump($location);
```
result:
```php
class AB\Iploka\Entity\Location#3 (12) {
  protected $city =>
  string(11) "Los Angeles"
  protected $continentCode =>
  string(2) "NA"
  protected $continentName =>
  string(13) "North America"
  protected $countryCode =>
  string(2) "US"
  protected $countryName =>
  string(13) "United States"
  protected $regionCode =>
  string(2) "CA"
  protected $regionName =>
  string(10) "California"
  protected $zip =>
  string(5) "90026"
  protected $latitude =>
  double(34.0766)
  protected $longitude =>
  double(-118.2646)
  protected $ip =>
  string(15) "134.201.250.155"
  protected $valid =>
  bool(true)
}
```

Get data as a simple array:
```php
$client = new AB\Iploka\Client('api_key');
$location = $client->get('134.201.250.155', true);
var_dump($location);
```
result:
```php
array(15) {
  ["ip"]=>
  string(15) "134.201.250.155"
  ["type"]=>
  string(4) "ipv4"
  ["continent_code"]=>
  string(2) "NA"
  ["continent_name"]=>
  string(13) "North America"
  ["country_code"]=>
  string(2) "US"
  ["country_name"]=>
  string(13) "United States"
  ["region_code"]=>
  string(2) "CA"
  ["region_name"]=>
  string(10) "California"
  ["city"]=>
  string(11) "Los Angeles"
  ["latitude"]=>
  float(34.003)
  ["longitude"]=>
  float(-118.4298)
  ["location"]=>
  array(8) {
    ["geoname_id"]=>
    int(4135386)
    ["capital"]=>
    string(10) "Washington"
    ["languages"]=>
    array(1) {
      [0]=>
      array(2) {
        ["code"]=>
        string(5) "en-US"
        ["name"]=>
        string(7) "English"
      }
    }
    ["country_flag"]=>
    string(43) "https://flagpedia.net/data/flags/h80/us.png"
    ["country_flag_emoji"]=>
    string(8) "🇺🇸  "
    ["country_flag_emoji_unicode"]=>
    string(15) "U+1F1FA U+1F1F8"
    ["calling_code"]=>
    string(1) "1"
    ["is_eu"]=>
    bool(false)
  }
}
```

#### Information
Available [params](https://github.com/GitHubHubus/ipstack-client/blob/master/src/OK/Ipstack/Entity/ParameterBag.php) for getting custom result

As example
```php
$client = new AB\Iploka\Client('api_key');
$client->getParams()->addField("calling_code");
```
