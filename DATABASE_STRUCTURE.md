```mermaid
erDiagram

    CLIENT ||--o{ DISP : has
    CLIENT }o--|| DISTRICT : lives_in
    ACCOUNT ||--o{ DISP : has
    ACCOUNT ||--o{ LOAN : owns
    ACCOUNT ||--o{ ORDER : makes
    ACCOUNT ||--o{ TRANS : makes
    DISP ||--o{ CARD : owns
    ACCOUNT }o--|| DISTRICT : located_in


    CLIENT {
        int client_id PK
        string birth_number
        int district_id FK
    }

    DISTRICT {
        int district_id PK
        string A2
        string A3
        string A4
        string A5
        string A6
        string A7
        string A8
        string A9
        string A10
        string A11
        string A12
        string A13
        string A14
        string A15
        string A16
    }

    ACCOUNT {
        int account_id PK
        int district_id FK
        string frequency
        date date
    }

    DISP {
        int disp_id PK
        int client_id FK
        int account_id FK
        string type
    }

    CARD {
        int card_id PK
        int disp_id FK
        string type
        date issued
    }

    LOAN {
        int loan_id PK
        int account_id FK
        date date
        float amount
        int duration
        float payments
        string status
    }

    ORDER {
        int order_id PK
        int account_id FK
        string bank_to
        string account_to
        float amount
        string k_symbol
    }

    TRANS {
        int trans_id PK
        int account_id FK
        date date
        string type
        string operation
        float amount
        float balance
        string k_symbol
        string bank
        string account
    }
```

# 🔗 Внешние ключи и связи между таблицами

| Таблица.Поле (FK)       | ↔ Таблица.Поле (PK)         | Тип связи           | Описание                                  |
|-------------------------|-----------------------------|---------------------|-------------------------------------------|
| `client.district_id`    | `district.district_id`      | многие-к-одному     | Клиент относится к одному району          |
| `account.district_id`   | `district.district_id`      | многие-к-одному     | Счёт зарегистрирован в одном районе       |
| `disp.client_id`        | `client.client_id`          | многие-к-одному     | Пользователь счёта                        |
| `disp.account_id`       | `account.account_id`        | многие-к-одному     | Привязка клиента к счёту                  |
| `card.disp_id`          | `disp.disp_id`              | один-к-одному/многим| Карта выдана держателю счёта              |
| `loan.account_id`       | `account.account_id`        | многие-к-одному     | Кредит привязан к счёту                   |
| `order.account_id`      | `account.account_id`        | многие-к-одному     | Платёжное поручение с конкретного счёта   |
| `trans.account_id`      | `account.account_id`        | многие-к-одному     | Транзакции по счёту                       |

