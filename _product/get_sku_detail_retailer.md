---
title: /api/products/skus/&ltsku_uuid&gt/
name: Get Sku Detail - Retailer
position: 2.24
type: get
description: Get Details about a SKU
right_code: |
  ~~~ json
  {
    "skus": [
      {
        "quantity": "54",
        "sku_id": "WONKYWILLA1"
      },
      {
        "quantity": "253",
        "sku_id": "CHOCO77"
      }
    ],
    "po_number": "po-tuuhBjSj",
    "notes": "here are some notes",
    "shipping_carrier": "UPS",
    "shipping_method": "Ground",
    "address": {
      "name": "Bob Iger",
      "business_name": "NBC",
      "address1": "30 Rockefeller Plaza",
      "address2": "STE 123",
      "city": "New York",
      "state": "NY",
      "postal_code": "10112"
    }
  }
  ~~~
  {: title="Request" }

  ~~~ json
  {
    "uuid": "9060814c-9feb-4a3e-958c-cb26d537cffc",
    "restrictions": null,
    "condition": "refurb",
    "distinguishing_attributes": {
      "size": 3
    },
    "item": {
      "uuid": "31adb57c-a40a-4a99-b3d0-3c6ccd8e8941"
    },
    "minimum_advertised_price": 10,
    "msrp": 43.65,
    "price_tiers": [
      {
        "shipping_cost_is_estimate": true,
        "cost": 100.12,
        "shipping_cost": 1.99,
        "minimum_tier_quantity": 2
      },
      {
        "shipping_cost_is_estimate": true,
        "cost": 75.6,
        "shipping_cost": 0.99,
        "minimum_tier_quantity": 4
      },
      {
        "shipping_cost_is_estimate": true,
        "cost": 49.99,
        "shipping_cost": 0,
        "minimum_tier_quantity": 16
      }
    ],
    "product_images": [
      {
        "uuid": "1929dd2b-ad2c-4021-9960-fb26e7bf448a",
        "url": "https://api.adorable.io/avatars/80/obad20.png",
        "width": 80,
        "height": 80
      },
      {
        "uuid": "8e6e1355-a185-4574-bb54-dc2193b9ab2d",
        "url": "https://api.adorable.io/avatars/285/obad39.png",
        "width": 285,
        "height": 285
      }
    ],
    "measurements": {
      "sku": {
        "weight": null,
        "length": null,
        "width": null,
        "height": null
      },
      "package": {
        "weight": null,
        "length": null,
        "width": null,
        "height": null
      }
    },
    "product_identifiers": {
      "upca": null,
      "ean13": null,
      "gtin14": null,
      "isbn": "9780765348272",
      "asin": "B000N2HBSO",
      "mpn": null
    },
    "inventory_lists": [
      {
        "uuid": "44a1f968-1ce8-4826-9cd9-f8a54f5d542d",
        "name": "The empty calendar inventory list"
      },
      {
        "uuid": "c9b32603-f6bf-4f49-89fd-8424399974f2",
        "name": "The enchanted act inventory list"
      },
      {
        "uuid": "868ea19d-5081-42ab-a4a5-c2337cd292af",
        "name": "The accessible motion inventory list"
      }
    ],
    "created": "2017-10-23T18:25:36.448007Z",
    "last_updated": "2017-10-23T18:25:36.448050Z",
    "sku_id": "voGDR4gOyYUOgcT7gw",
    "quantity_in_stock": 14,
    "quantity_on_backorder": 81,
    "number_of_units_bundled": 1,
    "minimum_advertised_price_currency": "USD",
    "msrp_currency": "USD"
  }
  ~~~
  {: title="Response" }

---
Get Details about a SKU. There is a varying amount of data provided with each SKUs. The Response Parameters listed below are potential attributes of SKUs that may be returned to you. Your username and password are optional as you can send your authorization token to receive this information.

### Response Parameters:

uuid
: (string) The Universal Unique Identifier for the SKU

restrictions
: (string) The Restrictions imposed on the SKU

condition
: (string) The Condition of the SKU; these include "new", "used", and "refurb"

distinguishing_attributes
: (object) The Distinguishing Attributes are attributes which based on a category or product line may be necessary to include. It may also be empty, as per the Suppliers' discretion.

item
: (object) The Item object contains the item_uuid; the item_uuid is the parent identifer for the sku_uuid.

minimum_advertised_price
: (number) The Minimum Advertised Price (MAP) is a price floor for advertisement on the SKU. You may not legally list the SKU for sale at a lower price.

msrp
: (number) The Manufacturer's Suggested Retail Price for the SKU. This is only a suggestion. It is not a price floor nor is it a price ceiling.

price_tiers
: (list) The list of Price Tier objects on this SKU including shipping_cost, minimum_tier_quantity, cost, shipping_cost_is_estimate.

product_images
: (list) The Product Images are a list of product image objects for the SKU which contain a uuid, url, width, and height of the image.

measurements
: (object) The Measurements object contains sku measurements object and a package measurements object.

product_identifiers
: (object) The Product Identifiers object contains the upca, ean13, gtin14, isbn, asin, and mpn for the SKU.

inventory_lists
: (list) The Inventory Lists list contains all of the Inventory List objects where this SKU currently resides.

created
: (string) The Created parameter indicates the date the SKU was Created in our system.

last_updated
: (string) The Last Updated parameter indicates the date the SKU was Last Updated in our system.

sku_id
: (string) The SKU Identifier for the SKU as provided by the Supplier

quantity_in_stock
: (number) The Quantity In-Stock parameter indicates how many SKUs are currently available for purchase.

quantity_on_backorder
: (number) The Quantity on Backorder parameter indicates how many of this particular SKU are going to be replenished. It can be considered a tentative quantity to be added to the current quantity in-stock.

number_of_units_bundled
: (number) The Number of Units Bundled parameter indicates how many SKUs are in a single bundle.

minimum_advertised_price_currency
: (string) The Minimum Advertised Price Currency parameter indicates what currency the MAP is based on.

msrp_currency
: (string) The Manufacturer's Suggested Retail Price Currency parameter indicates what currency the MSRP is based on.

#### Price Tier Object:

shipping_cost
: (number) The Shipping Cost per the SKU per the Price Tier

minimum_tier_quantity
: (number) The Minimum Tier Quantity per the SKU per the Price Tier

cost
: (number) The Cost per the SKU per the Price Tier

shipping_cost_is_estimate
: (boolean) The Shipping Cost is Estimate parameter answers the question whether the shipping cost is an estimate per the SKU per the Price Tier.

#### Product Image Object:

uuid
: (string) The Universal Unique Identifier for the SKU Product Image

url
: (string) The URL for the SKU Product Image

width
: (number) The Image Width in pixels for the SKU Product Image

height
: (number) The Image Height in pixels for the SKU Product Image

#### SKU Measurements Object:

weight
: (number) The Weight of the SKU in pounds (lbs.)

length
: (number) The Length of the SKU in inches

width
: (number) The Width of the SKU in inches

height
: (number) The Height of the SKU in inches

#### Package Measurements Object:

weight
: (number) The Weight of the packaged SKU in pounds (lbs.)

length
: (number) The Length of the packaged SKU in inches

width
: (number) The Width of the packaged SKU in inches

height
: (number) The Height of the packaged SKU in inches

#### Product Identifiers Object:

upca
: (string) The Universal Product Code type A (UPCA) is an 11-digit code used to identify the SKU.

ean13
: (string) The 13-digit European Article Number (EAN13) also known as the International Article Number is a 13-digit code used to identify the SKU.

gtin14
: (string) The 14-digit Global Trade Identification Number (GTIN14) also known as the Global Trade Item Number is a 14-digit code used to identify the SKU.

isbn
: (string) The International Standard Book Number (ISBN) is a unique numberic commercial book identifier. If the SKU is a book or can be classified as a book in some way shape or form, then an ISBN may be available for it.

asin
: (string) Amazon Standard Identification Number (ASIN) is the unique ID provided by the Amazon company. This number may be used to identify and match this SKU up to the proper listing on Amazon.com.

mpn
: (string) Manufacturer Part Number (MPN) is an identifier given to a part by the manufacturer. This number may be used to identify products such as car parts or computer parts that generally have sofisticated systems and readily available software for product management.

#### Inventory List Object:

uuid
: (string) The Universal Unique Identifier for the Inventory List

name
: (string) The Name your company has given to this Inventory List

Supplier Object:

uuid
: (string) The Universal Unique Identifier for the Supplier

name
: (string) The Supplier Name

| Code | Name                   | Meaning                                                                      |
|------|-------------------------------------------------------------------------------------------------------|
| 200  | OK                     | The API call was received and response is provided                           |
| 400  | Bad Request            | Generally, something required for the request is missing                     |
| 401  | Unauthorized           | Generally, the username or password is incorrect                             |
| 403  | Permission Denied      | Generally, the user does not have permission to perform the requested action |
| 404  | Not Found              | Generally, the call is not sent to the correct URL                           |
| 405  | Method Not Allowed     | Generally, the HTTP verb is not correct for the intended call                |
| 415  | Unsupported Media Type | Generally, this is a syntax problem                                          |


~~~ bash
curl "https://stable.projectthanos.com/api/products/skus/9060814c-9feb-4a3e-958c-cb26d537cffc/" \
     -H 'Authorization: Token a0f17278bed479ee719ea890b8caf0329e1f3e5b' \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{
  "address": {
    "state": "NY",
    "city": "New York",
    "address1": "30 Rockefeller Plaza",
    "business_name": "NBC",
    "postal_code": "10112",
    "name": "Bob Iger",
    "address2": "STE 123"
  },
  "shipping_carrier": "UPS",
  "po_number": "po-tuuhBjSj",
  "notes": "here are some notes",
  "skus": [
    {
      "quantity": "54",
      "sku_id": "WONKYWILLA1"
    },
    {
      "quantity": "253",
      "sku_id": "CHOCO77"
    }
  ],
  "shipping_method": "Ground"
}'

~~~
{: title="Curl" }

~~~ bash
http --json GET 'https://stable.projectthanos.com/api/products/skus/9060814c-9feb-4a3e-958c-cb26d537cffc/' \
    'Authorization':'Token a0f17278bed479ee719ea890b8caf0329e1f3e5b' \
    'Content-Type':'application/json; charset=utf-8' \
    address:="{
  \"state\": \"NY\",
  \"city\": \"New York\",
  \"address1\": \"30 Rockefeller Plaza\",
  \"business_name\": \"NBC\",
  \"postal_code\": \"10112\",
  \"name\": \"Bob Iger\",
  \"address2\": \"STE 123\"
}" \
    shipping_carrier="UPS" \
    po_number="po-tuuhBjSj" \
    notes="here are some notes" \
    skus:="[
  {
    \"quantity\": \"54\",
    \"sku_id\": \"WONKYWILLA1\"
  },
  {
    \"quantity\": \"253\",
    \"sku_id\": \"CHOCO77\"
  }
]" \
    shipping_method="Ground"

~~~
{: title="HTTPie" }

~~~ python
# Install the Python Requests library:
# `pip install requests`

import requests
import json


def send_request():
    # Get Sku Detail - Retailer
    # GET https://stable.projectthanos.com/api/products/skus/9060814c-9feb-4a3e-958c-cb26d537cffc/

    try:
        response = requests.get(
            url="https://stable.projectthanos.com/api/products/skus/9060814c-9feb-4a3e-958c-cb26d537cffc/",
            headers={
                "Authorization": "Token a0f17278bed479ee719ea890b8caf0329e1f3e5b",
                "Content-Type": "application/json; charset=utf-8",
            },
            data=json.dumps(    address:="{
  \"state\": \"NY\",
  \"city\": \"New York\",
  \"address1\": \"30 Rockefeller Plaza\",
  \"business_name\": \"NBC\",
  \"postal_code\": \"10112\",
  \"name\": \"Bob Iger\",
  \"address2\": \"STE 123\"
}" \
    shipping_carrier="UPS" \
    po_number="po-tuuhBjSj" \
    notes="here are some notes" \
    skus:="[
  {
    \"quantity\": \"54\",
    \"sku_id\": \"WONKYWILLA1\"
  },
  {
    \"quantity\": \"253\",
    \"sku_id\": \"CHOCO77\"
  }
]" \
    shipping_method="Ground")
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')

~~~
{: title="Python (requests)" }

~~~ javascript
// request Get Sku Detail - Retailer
(function(callback) {
    'use strict';

    const httpTransport = require('https');
    const responseEncoding = 'utf8';
    const httpOptions = {
        hostname: 'stable.projectthanos.com',
        port: '443',
        path: '/api/products/skus/9060814c-9feb-4a3e-958c-cb26d537cffc/',
        method: 'GET',
        headers: {"Authorization":"Token a0f17278bed479ee719ea890b8caf0329e1f3e5b","Content-Type":"application/json; charset=utf-8"}
    };
    httpOptions.headers['User-Agent'] = 'node ' + process.version;


    const request = httpTransport.request(httpOptions, (res) => {
        let responseBufs = [];
        let responseStr = '';

        res.on('data', (chunk) => {
            if (Buffer.isBuffer(chunk)) {
                responseBufs.push(chunk);
            }
            else {
                responseStr = responseStr + chunk;
            }
        }).on('end', () => {
            responseStr = responseBufs.length > 0 ?
                Buffer.concat(responseBufs).toString(responseEncoding) : responseStr;

            callback(null, res.statusCode, res.headers, responseStr);
        });

    })
    .setTimeout(0)
    .on('error', (error) => {
        callback(error);
    });
    request.write("{\"skus\":[{\"quantity\":\"54\",\"sku_id\":\"WONKYWILLA1\"},{\"quantity\":\"253\",\"sku_id\":\"CHOCO77\"}],\"po_number\":\"po-tuuhBjSj\",\"notes\":\"here are some notes\",\"shipping_carrier\":\"UPS\",\"shipping_method\":\"Ground\",\"address\":{\"name\":\"Bob Iger\",\"business_name\":\"NBC\",\"address1\":\"30 Rockefeller Plaza\",\"address2\":\"STE 123\",\"city\":\"New York\",\"state\":\"NY\",\"postal_code\":\"10112\"}}")
    request.end();


})((error, statusCode, headers, body) => {
    console.log('ERROR:', error);
    console.log('STATUS:', statusCode);
    console.log('HEADERS:', JSON.stringify(headers));
    console.log('BODY:', body);
});

~~~
{: title="Node.js" }