# Entity Relationship Diagram
This diagram has been created with [dbdiagram](https://dbdiagram.io/home).

```
Table User {
  id varchar [pk, note: 'uuid']
  name varchar [not null]
  email varchar [not null, unique]
  password varchar [not null]
}

Table Wallet {
  id varchar [pk, note: 'uuid']
  user varchar [ref: - User.id, not null] 
  value double [default: 0]
  updatedAt timestamp [note: 'When Wallet or Transaction created']
}

Table Transaction {
  id varchar [pk, note: 'uuid']
  user varchar [ref: > User.id, not null]
  wallet varchar [ref: > Wallet.id, not null]
  value double [not null]
  kind TransactionKind [not null]
  createdAt timestamp [note: 'When Transaction created']
}

Enum TransactionKind {
  in
  out
}
```