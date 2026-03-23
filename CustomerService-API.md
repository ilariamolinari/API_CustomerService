# Customer Service API #

Exmaple of an API that allows for customer management.
`http://DESKTOP-D0USMSR:8080`

## Endpoints ##

### GET customers ###

GET `/customer`

Returns list of all customers


### Filter customers by tiercode ###

GET `/customer?tiercode=#`

Filters all customers by tiercode where 

`#` = 1 -> Standard 

`#` = 2 -> Premium 

`#` = 3 -> ELite


### GET customer by customerID ###

GET `/customer/:id`

Get one single customer by knowing its customerid


### POST customers ###

POST `/customer`

Allow to insert new customer(s) in the customer database 

The request body needs to be in JSON format shown in the example.

```
POST /customer

{
    "customer": [
        {
            "name": "Marco",
            "surname": "Rossi",
            "phonenumber": "3333333333",
            "tiercode": "1",
            "createdate": "2023-01-30"
        }
    ]
}
```

NOTE: By using this method, customerid is automatically generated to avoid conflicts

### UPDATE customer ###

 Allows to overwrite all information about an existing customer by knowing its customerid.

 The request body needs to be in JSON format shown in the example.

```
PUT /customer

{
  "customer_id": [
    {
      "id": 17,
      "name": "Marco",
      "surname": "Rossi",
      "phonenumber": "3333333333",
      "tiercode": "1",
      "createdate": "2025-01-23"
    }
  ]
}
```
WARNING: This method overwrites existing customer information, be sure to insert correct ID.

WARNING2: If the ID is unassigned, this method insert a new customer with the chosen ID.

 




