# Contacts

> Path

```
/contacts
```

Points of contacts with customers/suppliers. Client portal registered users will each have a contact record associated with them.

## Contact Verbs

* GET

## Contact Fields

> Example Entity Response

```json
{
  "id": "/api/contacts/1",
  "type": "Contact",
  "attributes": {
    "id": 1,
    "fullName": "Billy Crystal",
    "emailAddress": "billy@gmail.com",
    "phoneNumber": "0129827394",
    "companyName": "Monsters Inc",
    "companyNumber": "0000000000",
    "vatNumber": "0000000000",
    "invoiceAddress": {
      "addressLineOne": "1 Monster Road", 
      "addressLineTwo": "Monster Town", 
      "townCity": "Monster City", 
      "region": "Monster County", 
      "postcode": "MM1 1EE", 
      "country": "UK"
    },
    "deliveryAddress": {
      "addressLineOne": "1 Monster Road", 
      "addressLineTwo": "Monster Town", 
      "townCity": "Monster City", 
      "region": "Monster County", 
      "postcode": "MM1 1EE", 
      "country": "UK"
    }
  }
}
```

Field | Type | Description
----- | ---  | -----------
id | int | Unique identifier
fullName | string | Full name of the contact
emailAddress | string | The contact's email address
phoneNumber | string | The contact's phone number
companyName | string | The name of the company the contact belongs to
companyNumber | string | The company number for the company the contact belongs to
vatNumber | string | The VAT number for the company the contact belongs to
invoiceAddress | object | The invoice address for the contact's company
deliveryAddress | object | The delivery address for the contact's company
