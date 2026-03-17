# Conto — Entity-Relationship Diagram (MVP)

> This ERD covers Sprints 1–4 only. Post-MVP entities (BankAccount, BankProfile, ImportBatch, PendingTransaction, TransactionSplit, GroceryLineItem, RecurringTransfer) will be added as their sprints begin.

```mermaid
erDiagram
    User ||--o{ AccountGroup : has
    AccountGroup ||--o{ VirtualAccount : contains
    VirtualAccount ||--o{ Transaction : holds
    User ||--o{ MerchantAlias : has

    User {
        bigint id PK
        string email UK
        string password_hash
        timestamp created_at
    }

    AccountGroup {
        bigint id PK
        bigint user_id FK
        string name
        decimal budget_limit
        string color
    }

    VirtualAccount {
        bigint id PK
        bigint group_id FK
        string name
        decimal balance
        decimal budget_limit
    }

    Transaction {
        bigint id PK
        bigint virtual_account_id FK
        decimal amount
        date date
        string description
        string display_name
    }

    MerchantAlias {
        bigint id PK
        bigint user_id FK
        string raw_bank_string
        string clean_name
        bigint suggested_account_id FK
    }
```
