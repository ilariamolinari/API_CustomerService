# Customer Service API #

Exmaple of an API that allows for customer management.

(Capire perchè non riesco a collegarmi da sito)

## Endpoints ##

### GET customers ###

GET `/customer`

Returns list of all customers in JSON format.


### Filter customers by tiercode ###

GET `/customer?tiercode=#`

Filters all customers by tiercode where 

`#` = 1 -> Standard 

`#` = 2 -> Premium 

`#` = 3 -> Elite


### GET customer by customerID ###

GET `/customer/:id`

Response returns one single customer with chosen customerid.


### POST customers ###

POST `/customer`

Allows to insert one or mutiple new custpmers in the customer database.

The request body needs to be in JSON format as shown in the example.

Example:
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

NOTE: customerid is automatically generated to avoid conflicts.

POST method also produces a csv file (PostedCustomers.csv) in which appends posted customers.
If the file does't exixts, it is created.


### UPDATE customer (PUT) ###

Allows to overwrite all information about one or multiple existing customers by knowing its customerid.

The request body needs to be in JSON format as shown in the example.

Example
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
Response body is in JSON format containing a list of string describing the outcome of the operation:

- "Cusomer # updated" if the update is successful.

- "Customer # not found" if the customer id is yet to be assigned.

WARNING: This method overwrites existing customer information, be sure to insert correct ID.


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
Response body is in JSON format containing a list of string describing the outcome of the operation:

- "Cusomer # updated" if the update is successful.

- "Customer # not found" if the customer id is yet to be assigned.

### DELETE CUSTOMER ###

DELETE `/customer/:id`

Allow to delete a customer by customerid.

Response body will be "Customer deleted" or "Customer not found" if customerid has no customer assigned.

# Nota per me: #

## Ancora da aggiungere ##

createdate (che ancora non si può modificare

e un catch per il conflitto su phonenumber che gia gestisce sql

