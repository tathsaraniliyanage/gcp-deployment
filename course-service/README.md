<a href="https://git.io/typing-svg"><img src="https://readme-typing-svg.herokuapp.com?font=Poppins&weight=500&size=60&pause=1000&center=true&vCenter=true&random=false&width=1200&height=80&lines=Course+Service" alt="Typing SVG" /></a>

[![Typing SVG](https://readme-typing-svg.herokuapp.com?size=32&vCenter=true&width=760&lines=🎓+Cloud+Deployment+with+GCP;)](https://git.io/typing-svg)


## 📌 Project Overview
This repository contains my assignment for Enterprise Cloud Architecture, demonstrating the deployment of a Spring Boot application with a MySQL database hosted on Google Cloud SQL.


## 📹 Demo Video
Watch the demo here: [Click Here](https://drive.google.com/file/d/1f6E1iepkVv4_7O9j-_uIAH3SU5axd5BO/view?usp=sharing)

> ⚡ Tip: Download the video for full HD quality if streaming appears blurry.


## 🌟 Google Cloud SQL (MySQL) Setup Guide

### Phase 1: Access Google Cloud Console
* Navigate to: https://console.cloud.google.com/sql
* Ensure the correct project is selected.

### Phase 2: Initialize Cloud SQL Instance
1. Select **Create Instance** → opt for **MySQL**.
2. Select **MySQL 8.0** (strongly recommended).
3. Assign an **Instance ID** (example: `mysqldb-instance`).
4. Configure the **root password** (example: `Mysql-ECA1!`).
5. Region selection: choose **us-central1** (or your nearest region).
6. Availability configuration: select **Single zone** for development purposes.

### Phase 3: Configure Public IP Access
1. Navigate to your instance → select **Connections** section.
2. Under **Public IP**, select **Add network**.
3. Provide name: `development-access`.
4. Set IP range to `0.0.0.0/0` (⚠️ **Development use only**).
5. Save configuration and copy the **Public IP** (example: `34.56.223.88`).

### Phase 4: Database Creation Within Instance
1. Launch Cloud Shell or local terminal and establish connection:

```bash
docker run -it --rm mysql:8 mysql -h <YOUR_PUBLIC_IP> -u root -p
```

Example connection:

```bash
docker run -it --rm mysql:8 mysql -h 35.188.214.104 -u root -p
```

Enter your configured password (`########`).

2. Execute database creation command:

```sql
CREATE DATABASE mysqldb;
```

3. Verify successful creation:

```sql
SHOW DATABASES;
```

The `mysqldb` database should appear in the list.

### Phase 5: Spring Boot Application Integration

Configure the `application-gcp.properties` file:

```properties
server.port=8081
spring.datasource.url=jdbc:mysql://43.250.243.42:3306/mysqldb?createDatabaseIfNotExist=true
spring.datasource.username=mysqldb
spring.datasource.password=########
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

Launch your Spring Boot application to establish connection with the Cloud SQL database.


## 🚀 Getting Started

1. Clone this repository:

```bash
git clone https://github.com/tathsaraniliyanage/gcp-deployment.git
```

2. Modify `application-gcp.properties` with your specific database configuration.

3. Run the Spring Boot application

4. Open the browser and navigate to `http://localhost:8081`.


## 🔖 License
This project is distributed under the [MIT License](LICENSE).. 


