### URL

###

POST /api/orders/supplier/<supplier_uuid>

### Request

```json
{
    "created_after": "2017-08-03T06:00:00.000Z",
    "created_before": "2017-07-31T06:00:00.000Z"
}
```

### Response

```json
{
  uuid: <uuid>,
  status: <string>,
  created_date: <datestring>,
  is_allocated: <bool>,
  purchase_order_id: <string>,
  notes: <string>,
  fees: {
    estimated_shipping_cost: <number>,
    drop_ship_fee: <number>,
    order_fee: <number>,
  },
  retailer: {
    name: <string>,
    uuid: <uuid>,
    user: {
      name: <string>,
      email: <string>,
    }
  },
  address: {
    name: <string>,
    business_name: <string>,
    address1: <string>,
    address2: <string>,
    city: <string>,
    state: <string>,
    postal_code: <string>,
  },
  requested_shipping: {
    shipping_carrier: <string>,
    shipping_method: <string>,
  },
  line_items: [
    {
      uuid: <uuid>,
      item_uuid: <uuid>,
      item_name: <string>,
      sku_uuid: <uuid>,
      sku_id: <string>,
      sku_name: <string>,
      supplier_uuid: <uuid>,
      supplier_name: <string>,
      cost: <number>,
      tracking_numbers: [
        {
          tracking_number: <string>,
          shipping_carrier: <string>,
          shipping_method: <string>,
          shipping_weight: <string>,
          shipping_cost: <number>,
          shipping_date: <datestring>,
        },
        ...
      ],
      allocation: {
        quantity_ordered: <int>,
        quantity_allocated: <int>,
        quantity_backordered: <int>,
        quantity_rejected: <int>,
        backordered_date: <datestring>,
      },
    },
  ],
}

```

### Status Code:
200 OK

### Error Status Codes:
400 Bad Request