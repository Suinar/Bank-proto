# Bank Proto

Shared Protocol Buffers definitions for the banking microservices.

This repository contains all gRPC contracts used for communication between services in the banking ecosystem. Keeping Protocol Buffer definitions in a dedicated repository ensures a single source of truth, simplifies versioning, and allows every microservice to use the same API contracts.

---

## Features

- Shared Protocol Buffers definitions
- gRPC service contracts
- Reusable request and response messages
- Common message definitions
- Versionable API contracts
- Easy integration across microservices

---

## Technologies

- Protocol Buffers (proto3)
- gRPC
- Go

---

## Repository Structure

```text
proto/
└── repository/
    ├── account/
    ├── card/
    ├── common/
    ├── credit/
    ├── currency/
    ├── deposit/
    ├── ranking/
    └── user/
```

---

## Used By

This repository is shared between the following microservices:

| Service | Description |
|---------|-------------|
| [Bank-repository-service](https://github.com/kVinsom/Bank-repository-service) | Repository microservice responsible for database operations |
| [Bank-exchange-rate-service](https://github.com/kVinsom/Bank-exchange-rate-service) | Exchange rate microservice responsible for currency rankings |

---

# Repository Service Contracts

The following services are provided by **Bank-repository-service**.

## UserRepository

| RPC | Description |
|-----|-------------|
| GetAll | Returns all users |
| GetById | Returns user by ID |
| GetByEmail | Finds user by email |
| GetByPhoneNumber | Finds user by phone number |
| Create | Creates a new user |
| Update | Updates user information |
| ChangePassword | Change user password by id |
| Delete | Deletes a user |

---

## AccountRepository

| RPC | Description |
|-----|-------------|
| GetAll | Returns all accounts |
| GetByUser | Returns accounts of a user |
| GetById | Returns account by ID |
| Create | Creates a new account |
| Blocking | Blocks an account |
| Close | Closes an account |
| Update | Updates account information |
| Delete | Deletes an account |

---

## CardRepository

| RPC | Description |
|-----|-------------|
| GetAll | Returns all cards |
| GetByUser | Returns user cards |
| GetById | Returns card by ID |
| GetByNumber | Finds card by number |
| Blocking | Blocks a card |
| Create | Creates a new card |
| Delete | Deletes a card |

---

## CreditRepository

| RPC | Description |
|-----|-------------|
| GetAll | Returns all credits |
| GetByUser | Returns user credits |
| GetById | Returns credit by ID |
| Create | Creates a new credit |
| Repay | Repays a credit |
| Delete | Deletes a credit |

---

## DepositRepository

| RPC | Description |
|-----|-------------|
| GetAll | Returns all deposits |
| GetByUser | Returns user deposits |
| GetById | Returns deposit by ID |
| Create | Creates a new deposit |
| Replenish | Adds funds to a deposit |
| Delete | Deletes a deposit |

---

## CurrencyRepository

| RPC | Description |
|-----|-------------|
| GetAll | Returns all currencies |
| GetById | Returns currency by ID |
| GetByIso | Finds currency by ISO code |
| GetBySymbol | Finds currency by symbol |
| Create | Creates a currency |
| Update | Updates currency |
| Delete | Deletes a currency |

---

# Exchange Rate Service Contracts

The following service is provided by **Bank-exchange-rate-service**.

## RankingRepository

| RPC | Description |
|-----|-------------|
| GetRelativeRanking | Returns exchange rate ranking for a currency pair |
| GetAllRanking | Returns all rankings for a base currency |

---

## Common Messages

Shared message used across multiple services.

| Message | Description |
|---------|-------------|
| Empty | Empty request/response |
| IdRequest | Entity identifier |
| UserIdRequest | User identifier |
| AmountRequest | Identifier and amount |

---

## Installation

Install the module in your Go project.

```bash
go get github.com/kVinsom/Bank-proto@latest
```

---

## Generate Go Code

```bash
protoc \
--proto_path=proto \
--go_out=proto \
--go_opt=paths=source_relative \
--go-grpc_out=proto \
--go-grpc_opt=paths=source_relative \
proto/repository/**/*.proto
```

## Why a Separate Proto Repository?

- Single source of truth for API contracts
- Shared by multiple microservices
- Independent versioning
- Prevents duplicated protocol definitions
- Easier maintenance
- Strongly typed communication between services

---
