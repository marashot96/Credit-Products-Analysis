# <div align = 'center'> Czech Bank Project  </div>

Здесь я привожу подробную реализацию проекта по работе клиентов банка. Увидеть другие мои проекты можно в [моем портфолио](https://github.com/marashot96/portfolio/blob/main/README.md).

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
```bash
Credit-Products-Analysis/
│
├── data/                        # Файлы с данными и описанием
│   ├── bank.csv
│   └── README_data.md
│
├── notebooks/                   # Jupyter-блокноты
│   ├── 01_EDA.ipynb             # Исследовательский анализ данных
│   ├── 02_Segmentation.ipynb    # Сегментация клиентов
│   ├── 03_Default_Predict.ipynb # Модель предсказания дефолта
│   └── 04_Report.ipynb          # Итоговая визуализация и выводы
│
├── sql/                         # SQL-запросы для анализа
│   ├── basic_insights.sql
│   └── loan_analysis.sql
│
└── README.md                    # Описание проекта
```

## 📁 Структура данных
Ниже приведена схема используемых в проекте csv-таблиц. Для более подробного изучения структуры таблиц можете перейти по этой ссылке - там приведено подробное их описание: [структура таблиц](https://github.com/marashot96/custs-behavioral-analysis/blob/main/DATABASE_STRUCTURE.md)

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
        int birth_number
        int district_id FK
    }

    DISTRICT {
        int district_id PK
        string A2
        string A3
        int A4
        int A5
        int A6
        int A7
        int A8
        int A9
        int A10
        int A11
        decimal A12
        decimal A13
        int A14
        int A15
        int A16
    }

    ACCOUNT {
        int account_id PK
        int district_id FK
        string frequency
        int date
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
        string issued
    }

    LOAN {
        int loan_id PK
        int account_id FK
        int date
        int amount
        int duration
        decimal payments
        string status
    }

    ORDER {
        int order_id PK
        int account_id FK
        string bank_to
        int account_to
        decimal amount
        string k_symbol
    }

    TRANS {
        int trans_id PK
        int account_id FK
        int date
        string type
        string operation
        decimal amount
        decimal balance
        string k_symbol
        string bank
        int account
    }
```

## 🔍 Источник данных
UCI Machine Learning Repository – [Bank Marketing](https://archive.ics.uci.edu/ml/datasets/Czech+Bank)

## 🚀 Быстрый старт
1. Склонируйте репозиторий
2. Установите зависимости `pip install -r requirements.txt`
3. Запустите Jupyter Notebook в `notebooks/`


---

## 💼 Контактная информация
Если вы хотите обсудить различные задачи, запросы или проекты, предложить кейс или сотрудничество — обязательно напишите мне!

- 📫 [t.me/marashot96](https://t.me/marashot96)
- 🌐 [marashot96@ya.ru](mailto:marashot96@ya.ru)

<div align="center">  <a href="https://github.com/marashot96/portfolio/blob/main/README.md#--маргарян-ашот---портфолио-"> Обо мне </a> </div>
