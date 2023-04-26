# monite_test
# Company customer
Learn how to register a customer of your company and assign a bank account to them before status changing.
## Overview
To start working with your customers, you need to register them, create bank accounts associated with them, and set their status as `active`.
### Register a customer
To register a new customer in your company, call `POST /customers`.
```

curl -X POST 'https://api.sandbox.monite.com/v1/customers' \
     -H 'X-Monite-Version: 2023-03-14' \
     -H 'X-Monite-Entity-Id: ENTITY_ID' \
     -H 'Authorization: Bearer ACCESS_TOKEN' \
     -H 'Content-Type: application/json' \
     -d '{
        "id": "123",
        "name": "John Foster",
        "email": "john@foster.com",
        "status": "not_active"
      }'

```
The successful response contains information about the customer created:
```

{
  "id": "123",
  "name": "John Foster",
  "email": "john@foster.com",
  "status": "not_active"
}

```
### Add a bank account to a customer
To add a bank account to a customer, call `POST /bank_accounts`.

```

curl -X POST 'https://api.sandbox.monite.com/v1/bank_accounts' \
     -H 'X-Monite-Version: 2023-03-14' \
     -H 'X-Monite-Entity-Id: ENTITY_ID' \
     -H 'Authorization: Bearer ACCESS_TOKEN' \
     -H 'Content-Type: application/json' \
     -d '{
        "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "iban": "GB33BUKB20201555555555",
        "bic": "GB33BUKB202",
        "name": "John Foster",
        "customer_id": "123"
       }'

```

The successful response contains information about the bank account created:
```

{
  "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "iban": "GB33BUKB20201555555555",
  "bic": "GB33BUKB202",
  "name": "John Foster",
  "customer_id": "123"
}

```
### Activate a customer
To set the customer's status as `active`, call `POST /customers/{customer_id}/set_as_active`.
```

curl -X POST 'https://api.sandbox.monite.com/v1/customers/{customer_id}/set_as_active' \
     -H 'X-Monite-Version: 2023-03-14' \
     -H 'X-Monite-Entity-Id: ENTITY_ID' \
     -H 'Authorization: Bearer ACCESS_TOKEN' \
     -H 'Content-Type: application/json' \
     -d '{
        "id": "123",
        "name": "John Foster",
        "email": "john@foster.com",
        "status": "set_as_active"
      }'

```
The successful response contains information about the customer's status activated:
```

{
  "id": "123",
  "name": "John Foster",
  "email": "john@foster.com",
  "status": "active"
}

