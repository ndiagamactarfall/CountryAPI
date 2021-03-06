![alt tag](https://raw.githubusercontent.com/fabian7593/CountryAPI/master/Files/imgsReadme/planetLogoAndText.png) 

A Rest Api of country information that you need.

EndPoint Request: [http://countryapi.gear.host/v1/Country/getCountries](http://countryapi.gear.host/v1/Country/getCountries)

**Suggestion: GearHost is a free hosting web apps, and has a limit of request by hour, I recommended download the repository and made your own server, and use this only for tests.
If you like the repository, my work, and you want that this works ever in the current host or other, please Donate, I will thanks you and the developers community too.**

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/c17666154d7a45af892e2b67a4639448)](https://www.codacy.com/app/fabian7593/CountryAPI?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=fabian7593/CountryAPI&amp;utm_campaign=Badge_Grade)
[![License](https://img.shields.io/badge/license-Apache%202-4EB1BA.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)

## Contents
### How to Use
- [What is CountryAPI](#what-is-countryapi)
- [Why use CountryAPI](#why-use-countryapi)
- [Executing the CountryAPI request](#executing-the-countryapi-request)
- [Request Parameters List](#request-parameters)
- [Request Examples (with parameters)](#request-examples)
   - [Specific country name](#specific-country-name)
   - [Countries with a specific region and subRegion](#countries-with-a-specific-region-and-subregion)
      - [Region and sub region list](#region-and-sub-region-list)
   - [Country with Alpha code 2 or 3](#country-with-alpha-code-2-or-3)
   - [Countries with english like native language](#countries-with-english-like-native-language)
   - [Countries with Currency code USD (United States Dollar)](#countries-with-currency-code-usd-united-states-dollar)
   - [Countries with an Area (km2) more than 8000 and less than 12000](#countries-with-an-area-km2-more-than-8000-and-less-than-12000)
   - [Countries with limit and pagination](#countries-with-limit-and-pagination)

### Buy me a Coffee (Donate)
- [Donate](#donate)

### Footer Docs
- [Servers](#servers) 
- [Current Version](#current-version) 
- [Credits](#credits) 
- [References](#references) 
- [Apache License](#license) 


<br>

## How To Use

#### What is CountryAPI?
Country API is a simple web service, made with REST API architecture, that return a simple Json Object with the verb "GET", withouth Oauth, Oauth2, or another authetication.

This service return the next data of all the countries in the world:

* **isSuccess:** If isSuccess is true, that means that all works fine, otherwise we had an error. 
* **userMessage:** This message is for the users, and only it is shown when isSuccess is false.
* **technicalMessage:** This message is technical, and only it is shown when isSuccess is false, please send us a stack trace.
* **totalCount:** The total countries found in our database.
* **response:** Array of countries.
   * name
   * alpha2Code
   * alpha3Code
   * nativeName
   * region
   * subRegion
   * latitude
   * longitude
   * area
   * numericCode
   * nativeLanguage
   * currencyCode
   * currencyName
   * currencySymbol
   * flag
   * flagpng


<br>

#### Why use CountryAPI?
* You don't need to create an account in any web page or application.
* You get a really simple json object.
* You get a basic information of any country.
* You get the flag image of the country.
* You don't need any type of authentication.
* You don't have limit of request (Not personally, but yes on server).
* It has the basic and importants features of RestAPI architecture.
* It has many params to request the service (included a pagination and limit).
* It's completely free and Open source.
* The service is always up (24/7).
* Feel free to use or contribute to improvement it.


<br>

#### Executing the CountryAPI request

Simple example.
Only need to open browser and paste the url [http://countryapi.gear.host/v1/Country/getCountries](http://countryapi.gear.host/v1/Country/getCountries).

Or use [Postman](https://www.getpostman.com/) or similar software with the verb GET, and obtain the json data and/or edit the json in [Json Editor Online](http://www.jsoneditoronline.org/).
For example:
![alt tag](https://raw.githubusercontent.com/fabian7593/CountryAPI/master/Files/imgsReadme/Postman.jpg)

#### Request Parameters
You can use any parameter that you need.

**Parameter list:**

| Name | Type | Required | SQLConsult Type |
| ---------- | ----------- | ------- | ------- |
| `pName` | String | False | `LIKE "% %"` | 
| `pAlpha2Code` | string | False | `Equals` | 
| `pAlpha3Code` | string | False | `Equals` | 
| `pNativeName` | string | False | `LIKE "% %"` | 
| `pRegion` | string | False | `Equals` | 
| `pSubRegion` | string | False | `Equals` | 
| `pAreaFrom` | long? | False | `BETWEEN pAreaFrom AND pAreaTo` | 
| `pAreaTo` | long? | False | `BETWEEN pAreaFrom AND pAreaTo` | 
| `pNumericCode` | long? | False | `Equals` | 
| `pNativeLanguage` | string | False | `Equals` | 
| `pCurrencyCode` | string | False | `Equals` | 
| `pCurrencyName` | string | False | `LIKE "% %"` | 
| `pPage` | int? | False | `Pagination` | 
| `pLimit` | int? | False | `Limit of objects response` | 

<br><br>
#### Request Examples
##### Specific country name 

[http://countryapi.gear.host/v1/Country/getCountries?pName=Costa%20Rica](http://countryapi.gear.host/v1/Country/getCountries?pName=Costa%20Rica)

` {"IsSuccess":true,"UserMessage":null,"TechnicalMessage":null,"TotalCount":1,"Response":[{"Name":"Costa Rica","Alpha2Code":"CR","Alpha3Code":"CRI","NativeName":"Costa Rica","Region":"Americas","SubRegion":"Central America","Latitude":"10","Longitude":"-84","Area":51100,"NumericCode":188,"NativeLanguage":"spa","CurrencyCode":"CRC","CurrencyName":"Costa Rican colón","CurrencySymbol":"₡","Flag":"https://api.backendless.com/2F26DFBF-433C-51CC-FF56-830CEA93BF00/473FB5A9-D20E-8D3E-FF01-E93D9D780A00/files/CountryFlags/cri.svg","FlagPng":"https://api.backendless.com/2F26DFBF-433C-51CC-FF56-830CEA93BF00/473FB5A9-D20E-8D3E-FF01-E93D9D780A00/files/CountryFlagsPng/cri.png"}]} `

PD: the request is similar with **pNativeName**.

<br>

##### Countries with a specific region and subRegion

[http://countryapi.gear.host/v1/Country/getCountries?pRegion=Americas&pSubRegion=Central%20America](http://countryapi.gear.host/v1/Country/getCountries?pRegion=Americas&pSubRegion=Central%20America)

###### Region and sub region list
* Africa
   * Eastern Africa
   * Middle Africa
   * Northern Africa
   * Southern Africa
   * Western Africa
* Americas
   * Caribbean
   * Central America
   * Northern America
   * South America
* Asia
   * Central Asia
   * Eastern Asia
   * South-Eastern Asia
   * Southern Asia
   * Western Asia
* Europe
   * Eastern Europe
   * Northern Europe
   * Southern Europe
   * Western Europe
* Oceania
   * Australia and New Zealand
   * Melanesia
   * Micronesia
   * Polynesia
* Polar

<br>

##### Country with Alpha code 2 or 3
[http://countryapi.gear.host/v1/Country/getCountries?pAlpha2Code=CR](http://countryapi.gear.host/v1/Country/getCountries?pAlpha2Code=CR)

##### Countries with english like native language
[http://countryapi.gear.host/v1/Country/getCountries?pNativeLanguage=eng](http://countryapi.gear.host/v1/Country/getCountries?pNativeLanguage=eng)

##### Countries with Currency code USD (United States Dollar)
[http://countryapi.gear.host/v1/Country/getCountries?pCurrencyCode=USD](http://countryapi.gear.host/v1/Country/getCountries?pCurrencyCode=USD)

##### Countries with an Area (km2) more than 8000 and less than 12000 
[http://countryapi.gear.host/v1/Country/getCountries?pAreaFrom=8000&pAreaTo=12000](http://countryapi.gear.host/v1/Country/getCountries?pAreaFrom=8000&pAreaTo=12000)

##### Countries with limit and pagination
[http://countryapi.gear.host/v1/Country/getCountries?pLimit=25&pPage=1](http://countryapi.gear.host/v1/Country/getCountries?pLimit=25&pPage=1)
[http://countryapi.gear.host/v1/Country/getCountries?pLimit=25&pPage=2](http://countryapi.gear.host/v1/Country/getCountries?pLimit=25&pPage=2)





<br><br>
## Donate
[![Donate](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=L25MKCRPR7TWY)

<br>

## Servers
#### PAAS: Host server .Net Web API 2.0
[https://www.gearhost.com/](https://www.gearhost.com/)

#### PAAS: Sql server 2008 free
[https://appharbor.com/](https://appharbor.com/)

#### BAAS: Free files storage
[https://backendless.com/](https://backendless.com/)

<br>

## Current Version
* **v1** `21/May/2017`

<br>

## Credits
**Author**
[Fabián Rosales - Frosquivel Developer](https://github.com/fabian7593)

**Contributors**
[List of contributors](https://github.com/fabian7593/CountryAPI/graphs/contributors)

[![alt tag](https://raw.githubusercontent.com/fabian7593/CountryAPI/master/Files/imgsReadme/github-logo.png)](https://github.com/fabian7593)
[![alt tag](https://raw.githubusercontent.com/fabian7593/CountryAPI/master/Files/imgsReadme/facebook.png)](https://www.facebook.com/fabian.rosales.509)
[![alt tag](https://raw.githubusercontent.com/fabian7593/CountryAPI/master/Files/imgsReadme/linkedin.png)](https://www.linkedin.com/in/fabian-rosales-esquivel-698893106/)
[![alt tag](https://raw.githubusercontent.com/fabian7593/CountryAPI/master/Files/imgsReadme/youtube.png)](https://www.youtube.com/channel/UCJnvvHb_vwMwbnZWplkHIfw)

<br>

## References

https://restcountries.eu

https://github.com/aredo/restcountries

<br>

## License
Copyright 2017 Fabian Rosales

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
<br><br>
