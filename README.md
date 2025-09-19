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


SQL → JSON Mapping

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


