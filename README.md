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










