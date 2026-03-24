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

`#` = 3 -> Elite


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

### UPDATE customer (PUT) ###

 Allows to overwrite all information about an existing customer by knowing its customerid.

 The request body needs to be in JSON format as shown in the example.

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

 ### UPDATE customer (PATCH) ###

 Allows to update only some information regarding a customer.

The request body needs to be in JSON format, as shown in the previous example (PUT) where the sole mandatory entry is "id".

Example to modfy phonenumber and tiercode of customer with ID=17:

```
PATCH /customer

{
  "customer_id": [
    {
      "id": 17,
      "phonenumber": "3333333333",
      "tiercode": "1"
    }
  ]
}
```


### DELETE CUSTOMER ###

DELETE `/customer/:id`

Allow to delete a customer by customerid.

Response body will be "Customer deleted" or "Customer not found" if customerid has no customer assigned.

# Nota per me: #

## Ancora da aggiungere ##

createdate (che ancora non si può modificare

throw per quando l customerid non esiste (non si può modificare un customer che non esiste)

e un catch per il conflitto su phonenumber che gia gestisce sql

aggiungere nella documentazione cosa esce dai vari metodi

Domani riscarica da qui che si è piantata di nuovo la macchina ciao
