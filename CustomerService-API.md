# Customer Service API #

Exmaple of an API that allows for customer management.
`http://DESKTOP-D0USMSR:8080`

## Endpoints ##

### Customers ###

GET `/customer`

Returns list of all customers

GET `/customer?tiercode=#`

Filters all customers by tiercode where 

`#` = 1 -> Standard 

`#` = 2 -> Premium 

`#` = 3 -> ELite
