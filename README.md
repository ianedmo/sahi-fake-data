# Sahi-Fake-Data

## Synopsis

Sahi Fake Data is a fake data API designed to be used with the [Sahi](http://sahipro.com/) automation tool.

There isn't really too much to it, you just include the fake-data-include.sah file into your sahi script and then you can call different functions to return different types of data, such as getFirstName() to return a first name. Of course, the easiest thing to do would be to store this in a variable, like the examples below show.

## Usage

There are two Sahi files within this repository - fake-data-include.sah and example.sah

The fake-data-include file needs to be included within the Sahi script that you create. You can do this using the following code:

```sh
_inlcude("fake-data-include.sah");
```

You are then able to call any of the functions within that include file. You'll find a list of them further down on this page.

The example.sah gives you an example of how to call the different functions. It stores the result of the different functions as variables and logs then in Sahi.

There is also a CSV folder that you'll need to place alongside your fake-data-include file. The CSV files contained within store most of the data that this API generates, so it is essential that these files are present.

When you implement this sahi-fake-data library into your project you'll likely want to do something more than just logging this information; you'll probably want to populate some fields with it. You'll find a code example below to show how that is done too.

## Code Example

### Example 1 - First Name
This example shows you how to generate a random first name.
```sh
_include("fake-data-include.sah");

var $firstName = getFirstName();
_log($firstName);
```
The above example would log the following:
```sh
Gordon
```

### Example 2 - Company Domain For Email Address
This example shows how to generate a first name, last name, company name and email address. The email address generated will be in the format of firstname.lastname@companyname.extension were the company name has all spaces and punctuation stripped from it and the extension is randomly selected.
```sh
_include("fake-data-include.sah");
var $firstName = getFirstName();
var $lastName = getLastName();
var $companyName = getCompany();
var $email = getEmail();
_log($firstName);
_log($lastName);
_log($companyName);
_log($email);
```
The above example would log the following:
```sh
Gordon
Peters
Stracke LTD
gordon.peters@strackeltd.net
```

### Example 3 - Specific Domain For Email Address
This example shows how to generate a first name, last name and email address, where you want the email to go to a specific location, in this case to the anonymous email service mailinator.com. The email function allows two parameters to be passed into it, the first being the domain name and the second being the domain extension.
```sh
_include("fake-data-include.sah");
var $firstName = getFirstName();
var $lastName = getLastName();
var $email = getEmail("mailinator", "com");
_log($firstName);
_log($lastName);
_log($email);
```
The above example would log the following:
```sh
Gordon
Peters
gordon.peters@mailinator.com
```

### Example 4 - Populating Form Fields
This example shows you how to use random data from this API to populate form fields on a website.
```sh
_include("fake-data-include.sah");

// Store Fake Data In Variables
var $firstName = getFirstName();
var $lastName = getLastName();
var $companyName = getCompany();
var $email = getEmail();
var $telephone = getTelephone();

// Complete Form Using Fake Data
_setValue(_textbox("First Name"), $firstName);
_setValue(_textbox("Last Name"), $lastName);
_setValue(_textbox("Company Name"), $companyName);
_setValue(_textbox("Email address"), $email);
_setValue(_textbox("Confirm Email address"), $email);
_setValue(_textbox("Telephone Number"), $telephone);
_click(_link("Submit"));
```

## Functions
Below is a list of functions that can be used to generate fake data.
* getTitle()
* getFirstName()
* getLastName()
* getCompany()
* getEmail($companyName, $domainSuffix)
* getStreet()
* getTown()
* getCity()
* getCounty()
* getPostcode()
* getEircode()
* getTelephone()

## Contributors
This work was inspired by and has used data definitions from:
- [Ian Edmondson](http://github.com/ianedmo/)'s Fake Data API
- [Marak](https://github.com/marak/Faker.js)'s Faker.js repository.
- https://github.com/stympy/faker/ - Copyright (c) 2007-2010 Benjamin Curtis
- http://search.cpan.org/~jasonk/Data-Faker-0.07/ - Copyright 2004-2005 by Jason Kohles

## License
[Sahi Fake Data](http://github.com/haselhurst/sahi-fake-data/) - Copyright (c) 2016 Michael Haselhurst

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
