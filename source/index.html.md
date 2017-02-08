---
title: API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='https://api.colisweb.com/'>Current Application</a>

includes:
  - errors

search: true
---

# Introduction

# Topic
## Authentication
## Errors
## Expanding Objects
## Idempotent Request
## Metadata
## Pagination
## Request IDs
## Versioning

# Core Resources
## Organizations
### The organization object
### Retrieve an organization
### List all organizations
## Users

## Shapes
A Shape is a GeoJSON feature object with type `Feature`, ee [geojson.org](http://geojson.org/geojson-spec.html#feature-objects).

A Shape has `properties` associated with the Geometry object.

### Postal Codes
> Postal Code Shape Structure

```json
{
    "id": "3",
    "geometry": {
        "type": "Point",
        "coordinates": [125.6, 10.1]
    },
    "properties": {
        "type": "postal_code",
        "postal_code": "59000",
        "insee_code": "59000",
        "city_name": "Lille",
        "name": "Euratechnolgies"
    }
}
```

## Invoices
Invoices are statements of what an organization owes to an other organization for a particular billing period, 
including subscriptions, invoice items, and any automatic proration adjustments if necessary.
[Stripe doc](https://stripe.com/docs/api#invoices)

## Invoice Items
Sometimes you want to add a charge or credit to a customer but only actually charge the customer's card at the end of 
a regular billing cycle. see [Stripe doc](https://stripe.com/docs/api#invoiceitems)

## Plans
A plan contains the pricing information for different services and feature levels provided by an organization.

## Subscriptions
Subscriptions allow an organization to charge an other organization on a recurring basis. 
A subscription ties a customer to a particular plan.

## Documents

# Transporters
## Vehicles
## Subcontracting Plans
A Subcontracting plan contains the pricing information for different tasks performed by an organization.

> Subcontracting Plans Structure

```json
{
    "id": "Paris Semaine",
    "type": "Feature",
    "geometry": {
      "type": "Polygon",
      "coordinates": [
        [
          [
            2.179412841796875,
            48.94775898298233
          ],
          [
            2.050323486328125,
            48.811385499847546
          ],
          [
            2.179412841796875,
            48.94775898298233
          ]
        ]
      ]
    },
    "properties": {
      "type": "standalone",
      "vehicle_type": "Moto",
      "variable_costs": [
        {
          "type": "day_of_week",
          "day": "MONDAY",
          "open": "08:00",
          "close": "17:00",
          "zone_id": "Europe/Paris",
          "cost": {
            "amount": 2.0,
            "currency": "EUR"
          }
        }
      ],
      "footprints": [
        {
          "additional_cost": {
            "amount": 4,
            "currency": "EUR"
          },
          "included_min": {
            "value": 0,
            "unit": "kgM"
          },
          "excluded_max": {
            "value": 30,
            "unit": "kgM"
          }
        },
        {
          "additional_cost": {
            "amount": 10,
            "currency": "EUR"
          },
          "included_min": {
            "value": 66,
            "unit": "kgM"
          },
          "excluded_max": {
            "value": 200,
            "unit": "kgM"
          }
        }
      ],
      "isochrones": [
        {
          "additional_cost": {
            "amount": -2,
            "currency": "EUR"
          },
          "included_min": {
            "value": 0,
            "unit": "m"
          },
          "excluded_max": {
            "value": 10,
            "unit": "m"
          }
        },
        {
          "additional_cost": {
            "amount": 3,
            "currency": "EUR"
          },
          "included_min": {
            "value": 20,
            "unit": "m"
          }
        }
      ],
      "slot_sizes": [],
      "lags": [],
      "effective_at": "2016-11-18T14:03:33+00:00",
      "expire_at": "2018-11-18T14:03:33+00:00"
    }
}
```
## Hubs
A specific shape reffering to an area or a location where a worker can start or end its shift.

## Workers
A worker is a user that can perform a workload. It must have a schedule, a hub and a vehicle.
A worker can also be associated with a subset of Subcontracting Plans in order to limit what kind of workloads, 
he or she can perform.

## Teams
A team is a group of users containing workers. 
Any team member or user with write permissions can swift workloads between members.


# Transportation
## Destinations
## Recipients
## Tasks
## Workloads
## Deliveries
## Tours

# Merchants
## Stock

# Notifications
## Devices
User's devices in an organization.

## Notifications
Notifications targeting a segment or individual users. You may target users in one of three ways using this method: 
by Organization, by User, or by Device. At least one targeting parameter must be specified.
See [OneSignal](https://documentation.onesignal.com/reference#create-notification)

# Webhooks



<!---

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

-->