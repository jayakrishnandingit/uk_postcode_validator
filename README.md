## Objective

UK Postcode Validator is a python wrapper that helps in validating and formatting UK postcodes. It uses open source APIs provided by https://postcodes.io.

## Pre-requisites

* python2.7 or 3.6

## How to install?

```
source myvenv/bin/activate
pip install uk-postcode-validator
```

## Usage

The library provides a `PostCodeClient` class with two public methods,

### `validate`

Method to validate a postcode and return formatted value from API.
On error, raises `ValidationError`.

### `format_code`

Alias for `validate` method.
This method is here only for explicit call for formatting.

### Examples

```
from uk_postcode_validator.client import PostCodeClient

client = PostCodeClient()
postcode = client.validate('M11AE')
print(postcode)  # "M1 1AE".

postcode = client.validate('695001')
ValidationError: Invalid postcode
```

You can get raw JSON output from Postcodes.io API by calling `get` method of the client class.

```
from uk_postcode_validator.client import PostCodeClient

client = PostCodeClient()
response = client.get('M11AE')
print(response)
{
    "status": 200,
    "result": {
        "postcode": "M1 1AE",
        ..
    }
}
response = client.get('695001')
print(response)
{
    "status": 404,
    "error": "Invalid postcode."
}
```
