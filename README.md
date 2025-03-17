# IT Mart

Nama : Ardhi Putra Pradana

NRP : 5027241022

Kelas : C

Asisten : NOPS

## ERD (Crow's Foot)

```mermaid
erDiagram
  employees {
    string id PK
    string name
    string phone UK
    string email UK
  }

  customers {
    string id PK
    string name
    string phone UK
    string email UK
    string address
  }

  suppliers {
    string id PK
    string name
    string phone UK
    string address
  }

  supplier_transactions {
    string id PK
    string supplier_id FK
    number total_price
    datetime transaction_date
    string status "pending, success, cancel"
  }

  supplier_transaction_items {
    string transaction_id PK, FK
    string product_id PK, FK
    number unit_price
    number quantity
  }

  categories {
    string id PK
    string name
    string description
  }

  products {
    string id PK
    string supplier_id FK
    string category_id FK
    string name
    string description
    string unit
    number price
    number quantity
  }

  orders {
    string id PK
    string customer_id FK
    string employee_id FK
    datetime order_date
  }

  order_items {
    string order_id PK, FK
    string product_id PK, FK
    number quantity
  }

  order_transactions {
    string id PK
    string order_id FK
    number total_price
    datetime transaction_date
    string payment_method "cash, credit_card, qris"
    string status "pending, success, cancel"
  }

  suppliers ||--o{ supplier_transactions : ""
  supplier_transactions ||--|{ supplier_transaction_items : ""
  products ||--o{ suppliers : ""
  products ||--o{ categories : ""
  orders ||--|{ order_items : ""
  orders ||--o{ customers : ""
  orders ||--o{ employees : ""
  order_items ||--o{ products : ""
  order_transactions ||--|| orders : ""
```