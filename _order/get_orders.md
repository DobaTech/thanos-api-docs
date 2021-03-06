---
title: /timp/orders/
name: Get Orders
position: 4.00
visibility: public
method: post
description: Get the Orders for your organization
right_code: |
  ~~~ json
  {
    "start": 0,
    "limit": 1
  }
  ~~~
  {: title="Request" }

  ~~~ json
  {
    "total_results": 142,
    "orders": [
      {
        "uuid": "319bba9f-71b1-4a93-8abf-67a45b8fdd5c",
        "is_allocated": false,
        "purchase_order_id": "8e5b1ccb-0221-4e26-a343-cd566bfe7419",
        "created_date": "2018-06-28T12:57:30.359784Z",
        "retailer_provided_order_notes": null,
        "supplier_provided_order_notes": null,
        "retailer_provided_order_attributes": null,
        "supplier_provided_order_attributes": null,
        "fees": {
          "estimated_shipping_cost": 0,
          "drop_ship_fee": 0,
          "order_fee": 0
        },
        "retailer": {
          "name": "projectthanos",
          "uuid": "ebf3657c-2abb-4aff-be70-69082acc9302",
          "user": {
            "name": "owner user",
            "email": "owneruser7@projectthanos.com"
          }
        },
        "address": {
          "name": "Megan King",
          "business_name": "Black-Rice",
          "address1": "08712 Villarreal Cliffs\nBishopchester, OK 45032",
          "address2": "9652 Richard Plains\nErikamouth, MP 22422-9361",
          "city": "Franklinbury",
          "state": "North Dakota",
          "postal_code": "85254",
          "phone_number": null,
          "country": "USA"
        },
        "requested_shipping": {
          "shipping_carrier": "UPS",
          "shipping_method": "Ground"
        },
        "invoices": [
        {
          "invoice_items": [
            {
              "sku_id": "56",
              "quantity_ordered": 10,
              "quantity_invoiced": 6,
              "supplier_order_number": "third",
              "invoice_item_attributes": [
                {
                  "attribute_name": "invoice item name",
                  "attribute_value": "can't believe we need invoice item attribute names and values"
                }
              ]
            }
          ],
          "invoice_number": "abcdef-ghi",
          "invoice_attributes": [
            {
              "attribute_name": "invoice attribute name",
              "attribute_value": "invoice attribute value"
            }
          ]
        }
      ],
        "line_items": [
      {
        "line_item_uuid": "5e91d918-67e8-4957-a69a-df9d2072ad9b",
        "status": "Unallocated",
        "line_item_designation": null,
        "item_uuid": "3bb5ef3b-2f1e-41da-bd85-1d6c746b0fa8",
        "item_name": null,
        "sku_uuid": "841ca56b-26f8-4d45-ac25-5b40d1da7354",
        "sku_id": "7FZvMyg0BjfewNJJ",
        "sku_name": null,
        "sku_title_variants": "None {}",
        "product_codes": {
          "upca": null,
          "ean13": null,
          "isbn": null,
          "gtin14": null,
          "asin": null,
          "mpn": null
        },
        "supplier_item_notes": null,
        "retailer_item_notes": null,
        "retailer_provided_sku_cost": 27.2,
        "supplier": {
          "uuid": "d6ac857d-c844-4312-8485-6d121d065308",
          "organization_name": "Stevens, Smith and Krause",
          "order_submitted_by": null
        },
        "supplier_provided_item_attributes": null,
        "retailer_provided_item_attributes": [
          {
            "attribute_name": "donut",
            "attribute_value": "jelly"
          }
        ],
        "tracking": [
        {
          "tracking_number": "12345",
          "shipping_carrier": "UPS",
          "shipping_method": "Speedy Ground",
          "shipping_weight": null,
          "shipping_cost": 3,
          "shipping_date": "2018-11-12",
          "created_date": "2018-11-10T17:47:07.872391Z",
          "quantity": 10,
          "package_attributes": [
            {
              "attribute_name": "package attribute name",
              "attribute_value": "package attribute value"
            }
          ]
        }
      ],
        "allocation": null
      }
  }
  ~~~
  {: title="Response" }

---
Get Orders matching certain criteria for your organization. This may contain any or all of your orders: completed, incomplete, processing, etc.


### Request Parameters:

start
: (int) The Start is the number of which "Order" you would like to start. If no other filters are used, the default order, which is date created, is used. The default Start value is 0. If this filter is not included in your request, the default value is used.

limit
: (int) The Limit is the element number of "Order" in your Orders List where you would like your results to end. If you have 10 orders and you limit at 8 and start at 4, only orders 4, 5, 6, 7, and 8 are included in the results.

sort
: (object) The Sort object contains a Key to sort on and a Direction (dir) to sort in.

line_item_allocation_statuses
: (array) One or more line item statuses. Possible choices include: `Unallocated`, `Partial`, or `Allocated`

line_item_designation
: (string) Line item status designation.  One of the following : `HasTracking`, `NeedsTracking`, `Backordered`, `Rejected`, `Cancelled`

start_date
: (string) The Start Date for your search results. The date must be written in the following format "YYYY-MM-DD hh:mm:ss"

end_date
: (string) The End Date for your search results. The date must be written in the following format "YYYY-MM-DD hh:mm:ss"

term
: (string) Term can be a word in the description of the sku to search for

po_number
: (string) The Retailer PO Number on the order

sent_to_supplier
: (boolean) True/False to request orders that have been sent to the supplier for fullfillment

org_uuids
: (array) An array of Organization Universal Unique Identifiers

##### Sort Object:

{% include timp/objects/sort.md %}

### Response Parameters:

total_results
: (number) The Total Results are the total order count per your oganization

orders
: (array) An array of order objects

#### Order Object:

{% include timp/orders/response/orders.md %}

#### Fees Object:

{% include timp/objects/fees.md %}

#### Retailer Object:

name
: (string) The Organization Name within your Retailer account

uuid
: (string) The Universal Unique Identifier for your Organization

user
: (object) The User object contains your name and email address; the name and email address of the user who submitted the Create Order API call.

#### Address Object:

{% include timp/objects/address_business.md %}

#### Requested Shipping Object:

{% include timp/orders/response/requested_shipping.md %}

#### Line Item Object:

{% include timp/objects/line_item.md %}

#### Tracking Numbers Object:

{% include timp/objects/tracking_number.md %}

#### Allocation Object:

{% include timp/objects/allocation.md %}

### Expected Response Codes

{% include timp/links/response_codes.md %}


~~~ bash
curl -X "POST" "https://api-sandbox.cruxconnect.com/timp/orders/" \
     -H 'Authorization: Token 1234567890' \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{
  "start": 0,
  "limit": 1
}'

~~~
{: title="Curl" }

~~~ bash
http --json POST 'https://api-sandbox.cruxconnect.com/timp/orders/' \
    'Authorization':'Token 1234567890' \
    'Content-Type':'application/json; charset=utf-8' \
    start:=0 \
    limit:=1

~~~
{: title="HTTPie" }

~~~ python
# Install the Python Requests library:
# `pip install requests`

import requests
import json


def send_request():
    # Get Orders
    # POST https://api-sandbox.cruxconnect.com/timp/orders/

    try:
        response = requests.post(
            url="https://api-sandbox.cruxconnect.com/timp/orders/",
            headers={
                "Authorization": "Token 1234567890",
                "Content-Type": "application/json; charset=utf-8",
            },
            data=json.dumps(    start:=0 \
    limit:=1)
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
// request Get Orders
(function(callback) {
    'use strict';

    const httpTransport = require('https');
    const responseEncoding = 'utf8';
    const httpOptions = {
        hostname: 'api-sandbox.cruxconnect.com',
        port: '443',
        path: '/timp/orders/',
        method: 'POST',
        headers: {"Authorization":"Token 1234567890","Content-Type":"application/json; charset=utf-8"}
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
    request.write("{\"start\":0,\"limit\":1}")
    request.end();


})((error, statusCode, headers, body) => {
    console.log('ERROR:', error);
    console.log('STATUS:', statusCode);
    console.log('HEADERS:', JSON.stringify(headers));
    console.log('BODY:', body);
});

~~~
{: title="Node.js" }
