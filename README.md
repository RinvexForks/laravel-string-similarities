# laravel-string-similarities

[![Latest Stable Version](https://poser.pugx.org/atomescrochus/laravel-string-similarities/v/stable)](https://packagist.org/packages/atomescrochus/laravel-string-similarities)
[![License](https://poser.pugx.org/atomescrochus/laravel-string-similarities/license)](https://packagist.org/packages/atomescrochus/laravel-string-similarities)
[![Total Downloads](https://poser.pugx.org/atomescrochus/laravel-string-similarities/downloads)](https://packagist.org/packages/atomescrochus/laravel-string-similarities)

Compare two string and get a similarity percentage. Note that I did not write the algorithms myself, see down this document for the full credits.

Some methods are usable in production, some are not, see usage for informations. Pull requests are more than welcomed!

## Install

You can install this package via composer:

``` bash
$ composer require atomescrochus/laravel-string-similarities
```

Then you have to install the package' service provider and alias:

```php
// config/app.php
'providers' => [
    ...
    Atomescrochus\StringSimilarities\StringSimilaritiesServiceProvider::class,
];
```

## Usage

``` php
$comparison = new \Atomescrochus\StringSimilarities\Compare();

// the functions returns similarity percentage between strings
$levenshtein = $comparison->levenshtein('first string', 'second string'); // Levenshtein comparison
$smg = $comparison->smg('first string', 'second string'); // Smith Waterman Gotoh comparison
$similar = $comparison->similarText('first string', 'second string'); // Using "similar_text()"

// This next one will return an array containing the results of all working comparison methods
// plus an array of 'data' that includes the first and second string, and the time in second it took to run all
// comparison. BE AWARE that comparing long string can results in really long compute time!
$all = $comparison->all('first string', 'second string');

// this one is not functional at the moment, use at your own risk if you do
// I have trouble adapting its code to PHP7.0 and up.
$jw = $comparison->jaroWinkler('first string', 'second string'); // Jaro Winkler comparison
```

## Change log

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Testing

Coming.

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) and [CONDUCT](CONDUCT.md) for details.

## Security

If you discover any security related issues, please email jp@atomescroch.us instead of using the issue tracker.

## Credits

- [Jean-Philippe Murray][link-author]
- [joshweir over StackOverflow](http://stackoverflow.com/a/38236357/1001942) for pointing me to the solutions and algorithms for the Jaro Winkler and Smith Waterman Gotoh comparison
- [All Contributors][link-contributors]

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
