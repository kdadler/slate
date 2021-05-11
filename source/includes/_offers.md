# Offers

> Path

```
/offers
```

Offers are product availability lists that are sent out to current or prospective customers.

## Offer Available Verbs

* GET

## Offer Fields

> Example Entity Response

```json
{
  "id": "/api/offers/OF-000-001",
  "type": "Offer",
  "attributes": {
    "id": 1,
    "idString": "OF-000-001",
    "name": "My offer",
    "description": "<p>I am describing the offer</p>",
    "status": "active",
    "conditionsOfSale": [
      {
        "type": "deliveryTerms",
        "typeLabel": "Delivery Terms",
        "value": "Ex works",
        "weight": 1,
        "label": null
      },
      {
        "type": "leadTime",
        "typeLabel": "Lead Time",
        "value": "5 weeks",
        "weight": 2,
        "label": null
      },
      {
        "type": "extraConditionsOfSale",
        "typeLabel": "Extra Condition",
        "value": null,
        "weight": 3,
        "label": "Take all"
      },
      {
        "type": "volumeDiscount",
        "typeLabel": "Volume Discount",
        "value": {
          "threshold": 10000,
          "discountPercentage": 5
        },
        "weight": 4,
        "label": null
      }
    ],
    "customerConditionsOfSale": [
      { "label": "Delivery Terms", "value": "Ex Works" },
      { "label": "Lead Time", "value": "5 weeks" },
      { "label": "Take All", "value": null },
      { "label": "Volume Discount", "value": "5% at €10,000" }
    ],
    "expiresOn": "2020-04-06T00:00:00.000Z",
    "currencyCode":  "EUR",
    "productCount": 5,
    "pricingTiers": [
        {"id": 1, "lowerThreshold":  0, "upperThreshold": 99, "discountPercentage": 0},
        {"id": 2, "lowerThreshold":  100, "upperThreshold": 239, "discountPercentage": 2},
        {"id": 3, "lowerThreshold":  240, "upperThreshold": null, "discountPercentage": 4}
    ],
    "columns": [
      {"id": 1, "type": "ean", "label": "EAN", "weight":  0, "enabled": true},
      {"id": 7, "type": "productName", "label": "Name", "weight":  1, "enabled": true},
      {"id": 239, "type": "brand", "label": "Brand", "weight":  2, "enabled": false},
      {"id": 53, "type": "stockCount", "label": "Stock Count", "weight":  3, "enabled": false},
      {"id": 54, "type": "cartonQuantity", "label": "Stock Count", "weight":  4, "enabled": true},
      {"id": 56, "type": "custom", "label": "My Custom Field", "weight":  5, "enabled": true}
    ],
    "sections": [
      {"id": 1, "label": "Fragrance", "weight": 10}
    ],
    "created": "2020-04-06T09:36:35.018Z",
    "shared": true,
    "sharedWithContacts": false,
    "sharedWithPublic": true,
    "shareKey": "s09dujsovd90sdvv",
    "shareLink": "www.client-portal.com/offer/s09dujsovd90sdvv",
    "recipientEmails": ["customer1@email.com", "customer2@email.com"],
    "recipientContacts": [
      {
        "contactId": 10,
        "contactName": "Sales Person",
        "companyId": 40,
        "companyName": "Customer Inc"
      },
      {
        "contactId": 15,
        "contactName": "Jon Bon Jovi",
        "companyId": 70,
        "companyName": "Vancouver Fragrances"
      }
    ],
    "productImagesShared": true,
    "stockQuantityLimit": 2000
  }
}
```

Field | Type | Description
----- | ---  | -----------
id | int | Unique identifier
idString | string | Unique identifier, in a human readable format
name | string | The offer's name 
description | string | HTML description 
status | string | The status token for the offer.
conditionsOfSale | array | The conditions of any sales made from products in this offer. Includes global discount criteria.
customerConditionsOfSale | array | The above conditions formatted for display to the customer
expiresOn | string&#124;null | Date of the expiry of the offer. 
currencyCode | string | Code of the currency that the offer is being made in
productCount | int | A count of the number of products in the offer.
pricingTiers | array | The pricing tiers in the offer
columns | array | The columns that are to be displayed on the offer's product table. Please see the columns section below for more information 
sections | array | The sections that products can be displayed in
created | string | Datetime that the offer was created
shared | bool | The master shared flag. This should be considered as an override to the below shared flags, they can be considered true only if this flag is also true.
sharedWithContacts | bool | Is this offer shared with contacts (existing customers)? If true, the recipient must login to view the offer.
sharedWithPublic | bool | Is this offer shared publicly. If true, the recipient may view the offer without a login
shareKey | string&#124;null | The unique key for the offer out. This is the key that is sent to prospective customers
shareLink | string&#124;null | The full link sent to prospective customers.
recipientEmails | array | A list of the email addresses that the offer has been shared with.
recipientContacts | array | A list of the customers (contacts) that the offer has been shared with.
productImagesShared | bool | Are the product images to be shared with the customer in this offer?
stockQuantityLimit | int | The upper limit of the stock quantity to display to the customer.

## Offer Customer Conditions of Sale

The customer conditions of sale are returned as an array of objects with label / value keys. The following rules should
be followed when rendering the conditions:

* They should be rendered in the order provided by the API
* If a condition's value is not null and not empty, it should be rendered as `{{ condition.label }} - {{ condition.value }}`
* If a condition's value is null or empty, it should be rendered as `{{ condition.label }}`

## Offer Columns

The `columns` key should contain an array of field definitions and their relative weights.

### Column Fields

Name | Type | Description
---- | ---- | -----------
id | int | The unique ID of the field. This ID will be unique across all offers
type | string | A slug that denotes the field type. See below for the types that exist
label | string | The human-readable label for the field
weight | int | The relative weight of the field. Fields should be displayed to a user in ascending weight order
enabled | bool | Is this field enabled? If false, the field should not be displayed to the end user. If this is not set, assume it to be true. 
  
### Column Types

Name | Description | Value source
---- | ----------- | ------------
ean | The EAN, or SKU of the line | A line's `ean` field
productName | The name of the line | A line's `name` field
brand | The branch of the line | A line's `brand` field
language | The language of the line | A line's `language` field
cartonQuantity | The carton quantity of the line | A line's `cartonQuantity` field
customValue | A custom value defined by the salesperson | Found in a line's `columnValues` field, find a match using the columns' `id` and line column values' `productColumnsId` values 
stockCount | The units of stock available for the line | Found in a line's `columnValues` field, look for the value with the type `stockCount`

## Offer Recipient Contacts

The `recipientContacts` key should contain an array of contacts that the offer has been shared with. Each should be formatted identically.

### Recipient Contact Fields

Name | Type | Description
---- | ---- | -----------
contactId | int | The unique ID of the contact that the offer has been shared with
contactName | string | The full name of the contact
companyId | int | The unique ID of the company that the contact belongs to
companyName | string | The company's name 

## Offer Statuses

Token | Label | Description | Visible to customers
----- | ----- | ----------- | --------------------
draft | Draft | The offer has been created but not yet available to order from | No
active | Active | The offer is currently active and available to be ordered from | Yes
expired | Expired | The offer has passed its expiry date | No
cancelled | Cancelled | The offer has been cancelled by the sales person | No

## Offer Index Parameters

Name | Type | Match | Default | Description
---- | ---- | ----- | ------- | -----------
name | string | partial | null | Search against the offer name
status | string | exact | null | Specify the status of the offers to be returned
contactId | boolean | exact | null | Filter offers out that are not shared with the specified contact ID
shared | boolean | exact | null | Filter offers based on the shared flag
sharedWithCustomers | boolean | exact | null | Filter offers based on the sharedWithCustomers flag
sharedWithPublic | int | exact | null | Filter offers based on the sharedWithPublic flag
order\[created] | string | exact | asc | Order the results by created date
order\[name] | string | exact | asc | Order the results by name
itemsPerPage | int | exact | 25 | The number of items to return per page
page | int | exact | 1 | The page of results to return

## Fetching an Offer

An offer may be fetched using either its ID (formatted or plain), or its share key value. Using the above data as an example,
any of the following are valid calls, and should return the same data:

* `/api/offers/1`
* `/api/offers/OF-000-001`
* `/api/offers/s09dujsovd90sdvv`

## Indexing Offers

For a customer to be permitted to view an offer, the following must be true:

* It must be shared
* It must be shared with customers
* It must have the status active
* It must be explicitly shared with the customer.

Below is an example request for this:

`/api/offers?shared=true&sharedWithCustomers=true&status=active&contactId=12345`

## Offers Subresources

> Example share request body

```json
{
  "emails": [
    "kieran@beautyneteurope.com",
    "theo@beautyneteurope.com"
  ]
}
```

The offers resource has the following subresources:

Name | Path | Method | Response | Description
---- | ---- | ------ | -------- | -----------
export-data | /api/offers/{id}/export-data | GET | XSLX file contents | Fetches the export file data for exporting an offer to an XLSX file.
share | /api/offers/{id}/share | PUT | Offer data | Shares the offer with another email. Requires the request body to include a non-empty emails value.
