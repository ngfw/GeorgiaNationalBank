[![Build Status](https://travis-ci.org/nikopeikrishvili/GeorgiaNationalBank.svg?branch=master)](https://travis-ci.org/nikopeikrishvili/GeorgiaNationalBank)


# NBG Rates
ეროვნული ბანკიდან კურსების ბიბლიოთეკა, ამჟამად აქვს 2 წყარო 
1. SOAP ვებ სერივის გამოყენებით 
2. RSS ის გამოყენებით 

## Install
```
composer require nikopeikrishvili/georgianationalbank:"dev-master"
```
***
## გამოყენება
```PHP
// მონაცემთა წყაროს მიღება ან იქნება SourceInterface ინსტანსი ან Exception
$data = \GeorgiaNationalBank\GeorgiaNationalBank::getDataSource();

// დოლარის კურსის მიღება ლართან მიმართებაში
$rate = $data->getRate(\GeorgiaNationalBank\Currencies::_USD);
echo $rate."\n";

// დოლარის კურსის მიღება რუბლთან მიმართებაში
$crossRate = $data->getCrossRate(\GeorgiaNationalBank\Currencies::_RUB, \GeorgiaNationalBank\Currencies::_USD);
echo $crossRate."\n";

// თანხის დათვლა რამდენი დოლარი იქნება 1 ლარი
$money = new \GeorgiaNationalBank\Money();
$money->fromCurrency = Currencies::_GEL;
$money->toCurrency = \GeorgiaNationalBank\Currencies::_USD;
$money->amount = 1;

// დაბრუნდება ისევ Money ობიექტი ოღონდ generatedAmount ში იქნება მნიშვნელობა
$amount = $data->calculateAmount($money);
```
