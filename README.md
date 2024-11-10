# Guvi-Project
Agricart
Agricart is an e-commerce platform connecting customers directly with farmers to provide fresh, seasonal fruits and vegetables free from preservatives. Agricart aims to improve health and flavor by offering products directly from farms, while enabling farmers to earn better prices for their produce.

Table of Contents
Introduction
Key Features
Technologies Used
Installation and Setup
Usage
Project Structure
Contributing
License
Introduction
Agricart is built to bridge the gap between farmers and consumers by providing a seamless, online shopping experience for fresh and seasonal produce. By eliminating preservatives, Agricart brings natural taste and quality to customers' tables, while benefiting farmers through fair pricing. This website is designed with user-friendly functionality that enables product browsing, adding items to a cart, and basic e-commerce management features.

Key Features
Product Listing - Browse available fruits and vegetables by category.
Detailed Product View - View product details like price, description, and stock availability.
Cart Management - Add, remove, and update quantities of items in your cart.
User Authentication - Secure sign-up and login for personalized shopping.
Direct Farmer Connection - Each product lists the farmer's details for transparency.
Responsive Design - Accessible on both desktop and mobile devices.
Technologies Used
Frontend: HTML, CSS, JavaScript
Backend: Spring Boot
Database: MySQL
Version Control: Git and GitHub
Installation and Setup
To set up Agricart locally, please follow these steps.

Prerequisites
Java JDK 8 or higher
MySQL
Maven
Git
A code editor, like VS Code or IntelliJ IDEA.
Clone the Repository
bash
Copy code
git clone https://github.com/yourusername/agricart.git
cd agricart
Database Setup
Open MySQL and create a new database named agricart.
Run the following commands to create the required tables:
sql
Copy code
CREATE DATABASE agricart;
USE agricart;

-- Example tables
CREATE TABLE users (
    user_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    address VARCHAR(255),
    phone VARCHAR(20)
);

CREATE TABLE farmers (
    farmer_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    contact_info VARCHAR(255)
);

CREATE TABLE products (
    product_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    category VARCHAR(100),
    price DECIMAL(10,2),
    description TEXT,
    stock_quantity INT,
    farmer_id INT,
    FOREIGN KEY (farmer_id) REFERENCES farmers(farmer_id)
);

CREATE TABLE carts (
    cart_id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    total_price DECIMAL(10,2),
    FOREIGN KEY (user_id) REFERENCES users(user_id)
);

CREATE TABLE cart_items (
    cart_item_id INT AUTO_INCREMENT PRIMARY KEY,
    cart_id INT,
    product_id INT,
    quantity INT,
    FOREIGN KEY (cart_id) REFERENCES carts(cart_id),
    FOREIGN KEY (product_id) REFERENCES products(product_id)
);
Update Database Configuration
In your application.properties file (found under src/main/resources), configure the following:

properties
Copy code
spring.datasource.url=jdbc:mysql://localhost:3306/agricart
spring.datasource.username=your_mysql_username
spring.datasource.password=your_mysql_password
spring.jpa.hibernate.ddl-auto=update
Build and Run
Open the terminal, navigate to the project root, and build the project using Maven:

bash
Copy code
mvn clean install
Run the project:

bash
Copy code
mvn spring-boot:run
Access the website at http://localhost:8080.

Usage
Home Page: Browse products by category or use the search bar.
Product Details: Click on a product to see details, including price, description, and farmer information.
Add to Cart: Select a product and click "Add to Cart" to add it to your shopping cart.
View Cart: Click on the cart icon to review selected items, adjust quantities, or remove items.
Checkout: Proceed to checkout (feature can be added in future versions).
Project Structure
plaintext
Copy code
agricart/
├── src/
│   ├── main/
│   │   ├── java/com/agricart/  # Java classes for controllers, services, models, etc.
│   │   ├── resources/
│   │   │   ├── application.properties  # Configuration settings
│   │   │   └── static/  # Static resources (HTML, CSS, JS)
│   │   └── templates/  # Thymeleaf templates (if used)
│   └── test/  # Unit and integration tests
├── pom.xml  # Maven dependencies
└── README.md
Contributing
Fork the Repository
Clone your fork:
bash
Copy code
git clone https://github.com/yourusername/agricart.git
Create a Branch for your feature or bug fix:
bash
Copy code
git checkout -b feature-name
Commit changes:
bash
Copy code
git commit -m "Add a descriptive commit message"
Push to your branch:
bash
Copy code
git push origin feature-name
Create a Pull Request on GitHub and wait for review.
License
This project is licensed under the MIT License. See the LICENSE file for details.

