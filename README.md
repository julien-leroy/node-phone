## What is node-phone?
`node-phone` is used to normalize the `mobile` phone number into a E.164 format.

The common problem is user normally input the phone number in this way:

```
`(817) 569-8900` or
`817569-8900` or
`1(817) 569-8900` or
`+1(817) 569-8900` or ...
```

What we want is always:

```
+18175698900
```

##FAQ

1. Does node-phone do any phone validation?

	Yes: If you provide the 2nd parameter (country), and the phone number do not start with `+` sign.

	`phone` will validate `phone_number_lengths` and `validation_begin_with`

	No: If the phone number start with `+` sign, even you pass the country.

	`phone` will simply remove all non digit and return `+XXXXXXXX` to you.

2. Why some of the number is valid, but return null?
	This npm is used to validate a mobile phone number for sending the SMS.
	So, we try to match all possible rule, such as area code, number prefix, etc. to test if it is a mobile phone number.
	However, some countries, like USA, we can only check if it is a valid `AREA CODE`, there is no mobile phone prefix.

	For UK, we know that mobile phone number is always start with `7`, in this case, this npm will be more helpful.

3. Why do you make this?

	Because we need to normalize the phone number for SMS notification for mobile phone only.

We don't validate if the number is mobile or not.


## Install
```
npm install phone
```

## Usage
```
var phone = require('phone');

phone('(817) 569-8900', ''); // return +18175698900
phone('(817) 569-8900', 'USA'); // return +18175698900
phone('(817) 569-8900', 'HKG'); // return null
phone('+1(817) 569-8900', HKG); // return +18175698900
phone('(817) 569-8900', ''); // return +18175698900
phone('6123-6123', ''); // return null, as default country is USA
phone('6123-6123', 'HKG'); // return +85261236123

```


## Test

```
npm test

``

## Help

We try to google for many results, but none of package can fit our need.
If you know that our rule is wrong, or can add more validation to make this npm more accurate.
Please open an issue and let us know.

## Change Log
* 0.0.5	Performance tuning, updated Iceland mobile format to 7 digits only.
* 0.0.4	Added US, CA area code to make it more accurate.


## License
MIT

