# Czech Bank Project 🏦

## 📌 Описание
Анализ банковской активности клиентов на основе открытого датасета Czech Bank. Исследуются транзакции, кредиты, поведение клиентов и потенциальные риски.

## 🎯 Цели проекта
- Провести разведочный анализ данных (EDA)
- Построить профили клиентов и сегментацию
- Оценить риски по займам
- Найти закономерности между транзакциями и дефолтами

## 🧰 Используемые технологии
- Python (Pandas, NumPy, Seaborn, Matplotlib)
- SQL (PostgreSQL)
- Jupyter Notebook

## 📁 Структура проекта
Ниже приведена схема используемых в проекте csv-таблиц. Для более подробного изучения структуры таблиц можете перейти по этой ссылке - там приведено подробное их описание: 

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

## 🔍 Источник данных
UCI Machine Learning Repository – [Bank Marketing](https://archive.ics.uci.edu/ml/datasets/Czech+Bank)

## 🚀 Быстрый старт
1. Склонируйте репозиторий
2. Установите зависимости `pip install -r requirements.txt`
3. Запустите Jupyter Notebook в `notebooks/`

