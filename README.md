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

## **Step 1: Download and Extract the Project**

<pre>
<b>Download the project:</b>
<code><button onclick="copyToClipboard('wget https://s3.amazonaws.com/klowdbay.com/YTCodeResources/book-seller.tar.gz')">📋 Copy</button>
wget https://s3.amazonaws.com/klowdbay.com/YTCodeResources/book-seller.tar.gz
</code>
</pre>

<pre>
<b>List files:</b>
<code><button onclick="copyToClipboard('ls')">📋 Copy</button>
ls
</code>
</pre>

<pre>
<b>Extract the tar file:</b>
<code><button onclick="copyToClipboard('tar -xzvf book-seller.tar.gz')">📋 Copy</button>
tar -xzvf book-seller.tar.gz
</code>
</pre>

<pre>
<b>List files again:</b>
<code><button onclick="copyToClipboard('ls')">📋 Copy</button>
ls
</code>
</pre>

<script>
function copyToClipboard(text) {
  navigator.clipboard.writeText(text);
  alert("Copied: " + text);
}
</script>
