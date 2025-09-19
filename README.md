# 📊 MoMo Transaction Dashboard

## 🧩 G-Ten 
## 👥 Team Members  
- Mbanza Teta Darcy  
- Aderline Gashugi 
- Henriette Biziyaremye 
- David Shumbusho

---

## 📌 Project Description  
This project processes **MoMo SMS transaction data** in XML format, cleans and categorizes it, stores it in a relational database, and provides a **web-based dashboard** to analyze and visualize transaction insights.  

---

## 🏛️ System Architecture  
We use an **ETL pipeline** to extract, transform, and load data into a database. The cleaned data is then used to generate analytics and visualizations on a simple dashboard.

**Architecture Diagram:**  
[🔗 View Diagram](<https://drive.google.com/file/d/13LnY_zU2YuJpSjdtIuyehOeo5_XLI9GL/view?usp=sharing>)

![System Architecture](assets/architecture.jpg)

---

## 📌 Scrum Board  
We are following **Agile** practices to organize and manage tasks using a Scrum board.

**Scrum Board Link:**  
[🔗 View Scrum Board](https://trello.com/b/915F2Fcc)


# 🗄️ Database Documentation
Our database is structured to capture **users, their phone numbers, MoMo transactions, transaction categories, and system logs**. This separation of entities ensures data normalization, avoids redundancy, and maintains consistency when processing large volumes of transactions. For instance:

- **Users and Phones** are separated into `USERS` and `USER_PHONES` tables because a user may have multiple phone numbers.  
- **Transactions** are stored in the `TRANSACTIONS` table, with foreign keys referencing both the **sender** and **receiver**.  
- **Categories** are stored in `TRANSACTION_CATEGORIES` to allow flexible classification of transactions (e.g., airtime, bill payment, transfer).  
- **Logs** are captured in `SYSTEM_LOGS` to track processing history.  
---

## 📑 Data Dictionary  

### USERS
| Column       | Type         | Description                     |
|--------------|-------------|---------------------------------|
| user_id (PK) | INT AUTO     | Unique identifier for a user    |
| user_name    | VARCHAR(100) | Name of the user                |
| email        | VARCHAR(150) | User email (optional)           |
| created_at   | TIMESTAMP    | Account creation timestamp      |

### USER_PHONES
| Column             | Type         | Description                                |
|--------------------|-------------|--------------------------------------------|
| phone_id (PK)      | INT AUTO     | Unique identifier for a phone record       |
| user_id (FK)       | INT          | References USERS(user_id)                  |
| phone_number       | VARCHAR(20)  | Phone number linked to the user            |

### TRANSACTION_CATEGORIES
| Column             | Type         | Description                                |
|--------------------|-------------|--------------------------------------------|
| category_id (PK)   | INT AUTO     | Unique identifier for category             |
| category_name      | VARCHAR(50)  | Name of category (e.g., Transfer, Airtime) |
| description        | TEXT         | Additional details about the category      |

### TRANSACTIONS
| Column             | Type         | Description                                |
|--------------------|-------------|--------------------------------------------|
| transaction_id (PK)| INT AUTO     | Unique identifier for a transaction        |
| amount             | DECIMAL(10,2)| Amount transacted                          |
| transaction_date   | TIMESTAMP    | Date and time of transaction               |
| sender_id (FK)     | INT          | References USERS(user_id) – sender         |
| receiver_id (FK)   | INT          | References USERS(user_id) – receiver       |
| category_id (FK)   | INT          | References TRANSACTION_CATEGORIES          |

### SYSTEM_LOGS
| Column             | Type         | Description                                |
|--------------------|-------------|--------------------------------------------|
| log_id (PK)        | INT AUTO     | Unique identifier for a log                |
| log_message        | TEXT         | Description of the processing step         |
| log_stamp          | TIMESTAMP    | When the log entry was created             |

---

## 💾 SQL → JSON Mapping  

| **SQL Table.Column**                   | **JSON Field**                  |
| -------------------------------------- | ------------------------------- |
| `USERS.user_id`                        | `user.user_id`                  |
| `USERS.user_name`                      | `user.user_name`                |
| `USERS.email`                          | `user.email`                    |
| `USERS.created_at`                     | `user.created_at`               |
| `USER_PHONES.phone_number`             | `user.phones[]`                 |
| `TRANSACTIONS.transaction_id`          | `transaction.transaction_id`    |
| `TRANSACTIONS.amount`                  | `transaction.amount`            |
| `TRANSACTIONS.transaction_date`        | `transaction.transaction_date`  |
| `TRANSACTIONS.sender_id`               | `sender.user_id`                |
| `TRANSACTIONS.receiver_id`             | `receiver.user_id`              |
| `TRANSACTIONS.category_id`             | `category.category_id`          |
| `TRANSACTION_CATEGORIES.category_name` | `category.category_name`        |
| `TRANSACTION_CATEGORIES.description`   | `category.description`          |
| `SYSTEM_LOGS.log_id`                   | `processing_logs[].log_id`      |
| `SYSTEM_LOGS.log_message`              | `processing_logs[].log_message` |
| `SYSTEM_LOGS.log_stamp`                | `processing_logs[].log_stamp`   |


