# Book Seller Project Deployment

This project is an **E-commerce Book Seller Application** deployed on **AWS Elastic Beanstalk**, with data stored in an **Amazon Aurora MySQL** database.

## **Project Overview**
- The homepage displays a **list of authors**.
- Users can select an author to **view books and prices**.
- Clicking "Order" shows a **Thank You** message.
- **Database**: Stores books, prices, and authors.
- **Deployment**: Uses AWS services like **Elastic Beanstalk, S3, and RDS (Aurora MySQL).**

---

## **Prerequisites**
Before starting, ensure you have the following:
- **AWS CLI installed and configured**
- **Java JDK 13 installed**
- **Apache Maven installed**
- **MySQL Client installed**

---

## **Setup and Deployment Steps**

## **Cloudshell**

## **Step 1: Download the Project Source Code**
```bash
wget https://s3.amazonaws.com/klowdbay.com/YTCodeResources/book-seller.tar.gz
```
Extracts the compressed project files
```bash
tar -xzvf book-seller.tar.gz
```
List the files
```bash
ls
```


## **Step 2: Verify the Directory Structure**
```bash
tree .
```
If tree is not installed, install it using:
```bash
sudo apt install tree -y  # For Ubuntu/Debian
sudo yum install tree  # For Amazon Linux
sudo snap install tree  # Alternative installation
```


## **Step 3: Install Java JDK 13**
```bash
wget https://download.java.net/java/GA/jdk13.0.1/cec27d702aa74d5a8630c65ae61e4305/9/GPL/openjdk-13.0.1_linux-x64_bin.tar.gz
```
Extracts Java JDK 13
```bash
tar -xvf openjdk-13.0.1_linux-x64_bin.tar.gz
```
Move Java JDK 13 to /opt/
```bash
sudo mv jdk-13.0.1 /opt/
```
Sets Java paths and verifies installation.
```bash
JAVA_HOME='/opt/jdk-13.0.1'
```
```bash
PATH="$JAVA_HOME/bin:$PATH"
```
```bash
export PATH
```
```bash
java -version
```


## **Step 4: Install Apache Maven**
Downloads and extracts Maven to /opt/
```bash
wget https://dlcdn.apache.org/maven/maven-3/3.9.9/binaries/apache-maven-3.9.9-bin.tar.gz
```
```bash
tar -xvf apache-maven-3.9.9-bin.tar.gz
```
```bash
sudo mv apache-maven-3.9.9 /opt/
```
Configures Maven and verifies installation.
```bash
M2_HOME='/opt/apache-maven-3.9.9'
```
```bash
PATH="$M2_HOME/bin:$PATH"
```
```bash
export PATH
```
```bash
mvn -v
```


## **Step 5: Navigate to Project Directory**
Moves into the project directory.
```bash
cd book-seller
```
```bash
ls
```

Navigate to Web Application Files: 
Lists all front-end web files (HTML/JSP).
```bash
cd ~/book-seller/src/main/webapp
```
```bash
ls
```
View a sample JSP file:
```bash
cat index.jsp
```
```bash
cat order.jsp
```


## **Step 6: Build and Package the Project**
Builds the project and generates a .war file inside the target folder.
```bash
cd ~/book-seller
```
```bash
mvn clean package
```
```bash
ls
```
```bash
ls ~/book-seller/target
```


## **Step 7: Create an AWS S3 bucket (or use an existing one) in AWS**
Copy warfile to the S3 bucket. When you create beanstalk platform, you can upload the code from the S3 bucket.

## **Upload .war File to an AWS S3 bucket**
Uploads the packaged .war file to an S3 bucket for AWS Elastic Beanstalk deployment.
```bash
aws s3 cp ~/book-seller/target/book-seller-1.0.0.war s3://<your-bucket-name>/ForBeanstalk/
```


## **Step 8: Deploy the Project on AWS Elastic Beanstalk**
1. Go to the AWS Elastic Beanstalk Console.
2. Click Create Application → Name it like book-seller-101.
3. Choose Tomcat as the platform.
4. Upload the .war file from your S3 bucket.
5. Click Deploy → Wait for ~10 minutes.


## **Step 9: Set Up the Database (Aurora MySQL)**
1. Go to the AWS RDS Console.
2. Click Create Database.
3. Select Aurora-MySQL.
4. Settings:
   - DB Cluster Identifier: yourname-book-seller
   - Master Username: <username>
   - Password: <***>
   - Instance Type: db.t3.small
   - Public Access: Yes
   - Security Group: Allow port 3306 from 0.0.0.0/0.
5. Click Create Database → Wait 10 minutes.


## **Step 10: Connect to AWS RDS MySQL Database**
```bash
mysql -h <your-db-endpoint> -P 3306 -u <username> -p
```
Once inside MySQL, create the database:
```bash
CREATE DATABASE ebdb;
```
```bash
USE ebdb;
```
Create a Books Table:
```bash
CREATE TABLE books (
    book_id INT AUTO_INCREMENT,
    title VARCHAR(250) NOT NULL,
    author VARCHAR(50),
    Price FLOAT,
    Qty INT,
    PRIMARY KEY (book_id)
) ENGINE = InnoDB;
```
Insert sample data:
```bash
INSERT INTO books (book_id, title, author, Price, Qty)
VALUES (1100, 'Chamber of Secrets', 'Rowling', 11.11, 4),
(1103, 'Philosophers Stone', 'Rowling', 10.90, 8),
(1105, 'War and Peace', 'Tolstoy', 22.22, 2),
(1107, 'Romeo and Juliet', 'Shakespear', 33.33, 5),
(1109, 'Othallo', 'Shakespear', 13.99, 7),
(1102, 'KingLear', 'Shakespear', 10.79, 3),
(1111, 'Death on the Nile', 'Agatha', 44.4, 15),
(1113, 'ABC Murders', 'Agatha', 39.4, 11),
(1115, 'Anna Kareneena', 'Tolstoy', 55.55, 23);
```
Check if the table is created:
```bash
SHOW TABLES;
```
```bash
SELECT * FROM books;
```


## **Step 11: Link Elastic Beanstalk to RDS**
1. Go to Elastic Beanstalk Console.
2. Click Environment → Configuration.
3. Under Software, click Edit.
4. Add the following Environment Properties:
   - RDS_USERNAME: <username>
   - RDS_PASSWORD: <***>
   - RDS_PORT: 3306
   - RDS_HOSTNAME: <your-db-endpoint.rds.amazonaws.com>
   - RDS_DB_NAME: ebdb
5. Click Apply → Wait for updates.


## **Step 12: Access Your Application**
1. Go to the Beanstalk Console.
2. Copy the Application URL (e.g., http://book-seller.us-east-1.elasticbeanstalk.com/).
3. Open it in a browser and test:
   - Select an author.
   - View book list.
   - Place an order.
   - Check database updates.


