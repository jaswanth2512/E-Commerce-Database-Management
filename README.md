# E-commerce Database Management System

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![Database](https://img.shields.io/badge/Database-Design-blue?style=for-the-badge)
![SQL](https://img.shields.io/badge/SQL-DDL%20%26%20DML-green?style=for-the-badge)

A comprehensive database management system designed for e-commerce platforms, featuring robust data modeling, normalization, and efficient query processing. This project demonstrates advanced database design principles and PostgreSQL implementation for handling online marketplace operations.

## 🎯 Project Overview

This project focuses on developing a scalable and efficient database management system for an e-commerce platform similar to eBay. The system handles the complete lifecycle of online transactions, from user registration to order delivery, ensuring data integrity and optimal performance.

## ✨ Key Features

### 🔐 User Management

- **Dual User Roles**: Support for both buyers and sellers
- **Profile Management**: Comprehensive user profiles with contact information
- **Authentication**: Secure user authentication system
- **Bank Integration**: Seller bank account management for payments

### 📦 Product Management

- **Product Catalog**: Detailed product listings with descriptions and images
- **Category System**: Hierarchical categorization with categories and subcategories
- **Inventory Tracking**: Real-time inventory management
- **Rating System**: Product and seller rating functionality
- **Watchlist**: Users can watch products for future reference

### 🛒 Shopping Experience

- **Shopping Cart**: Persistent cart functionality
- **Order Processing**: Complete order management system
- **Payment Integration**: Transaction tracking and payment processing
- **Shipping Management**: Comprehensive shipping and delivery tracking

### 📊 Analytics & Reviews

- **Review System**: Buyer-to-seller and product reviews
- **Rating Analytics**: Average rating calculations
- **Order Tracking**: Real-time order and delivery status
- **Inventory Analytics**: Product availability and sales tracking

## 🏗️ System Architecture

### Database Design Approach

1. **Entity-Relationship Modeling**: Comprehensive ER diagram design
2. **Normalization**: Database normalized to BCNF (Boyce-Codd Normal Form)
3. **Functional Dependencies**: Well-defined attribute relationships
4. **Referential Integrity**: Strong foreign key relationships

### Core Entities

- **Users**: Buyers and sellers with specialized attributes
- **Products**: Catalog items with categories and inventory
- **Orders**: Transaction records with payment and shipping details
- **Reviews**: Rating and feedback system
- **Shipping**: Delivery tracking and logistics management

## 📁 Project Structure

```
E-commerce_Database_Design/
├── DBMS_Project_ER_Diagram.pdf          # Entity-Relationship diagram
├── DBMS_Project_Relational_Schema.pdf   # Relational schema design
├── DBMS_Project_FDs_and_BCNF.pdf       # Functional dependencies and normalization
├── Minimal_FD_Set.pdf                   # Minimal functional dependency set
├── DDL_Script.sql                       # Database schema creation script
├── Dummy_Data_Insertion_Script.sql      # Sample data insertion
├── Sample_Queries.sql                   # Example queries and operations
└── README.md                            # Project documentation
```

## 🚀 Getting Started

### Prerequisites

- PostgreSQL 12 or higher
- pgAdmin (optional, for GUI management)
- Basic understanding of SQL and database concepts

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/PrathamPatel25/E-commerce_Database_Design
   cd E-commerce_Database_Design
   ```

2. **Set up PostgreSQL database**

   ```sql
   CREATE DATABASE ecommerce_db;
   ```

3. **Execute the DDL script**

   ```bash
   psql -U your_username -d ecommerce_db -f DDL_Script.sql
   ```

4. **Insert sample data**

   ```bash
   psql -U your_username -d ecommerce_db -f Dummy_Data_Insertion_Script.sql
   ```

5. **Test with sample queries**
   ```bash
   psql -U your_username -d ecommerce_db -f Sample_Queries.sql
   ```

## 📊 Database Schema

### Key Tables

| Table              | Description                                |
| ------------------ | ------------------------------------------ |
| `user_profile`     | User authentication and basic information  |
| `user`             | User identification and profile linking    |
| `buyer`            | Buyer-specific information                 |
| `seller`           | Seller-specific information and ratings    |
| `product`          | Product catalog with pricing and inventory |
| `order`            | Order management and tracking              |
| `payment`          | Transaction records                        |
| `shipping_address` | Delivery address management                |
| `shipping_status`  | Order tracking and delivery status         |

### Relationships

- **User Specialization**: Users can be buyers, sellers, or both
- **Many-to-Many**: Products ↔ Categories, Users ↔ Watchlist, Orders ↔ Products
- **One-to-Many**: Sellers → Products, Orders → Payments
- **Hierarchical**: Categories → Subcategories

## 🔍 Sample Queries

### Fetch Sellers with the Most Products Listed

```sql
SELECT s.user_id, s.item_sold, COUNT(p.product_id) AS product_count
FROM seller s
JOIN product p ON s.user_id = p.product_seller_id
GROUP BY s.user_id, s.item_sold
ORDER BY product_count DESC
LIMIT 10;
```

### Fetch Sellers with Products Sold Out:

```sql
SELECT s.user_id, s.item_sold
FROM seller s
JOIN product p ON s.user_id = p.product_seller_id
WHERE p.available_units = 0;
```

### Fetch Orders and Their Shipping Status:

```sql
SELECT o.order_id, ss.tracking_id, ss.delivery_status
FROM "order" o
LEFT JOIN shipping_status ss ON o.order_id = ss.order_id;
```

## 📈 Database Features

### Normalization Benefits

- **Data Integrity**: Eliminates redundancy and ensures consistency
- **Storage Efficiency**: Optimized storage through proper normalization
- **Update Anomalies**: Prevents data inconsistencies during updates
- **BCNF Compliance**: Ensures every determinant is a candidate key

### Performance Optimizations

- **Query Optimization**: Efficient joins and subqueries
- **Referential Integrity**: Fast foreign key lookups
- **Data Types**: Appropriate data types for optimal storage

## 🛠️ Technical Implementation

### Database Design Process

1. **Requirements Analysis**: Identified e-commerce system requirements
2. **Conceptual Design**: Created comprehensive ER diagram
3. **Logical Design**: Converted to relational schema
4. **Normalization**: Applied normalization rules through BCNF
5. **Physical Design**: Implemented in PostgreSQL with optimizations

### Key Design Decisions

- **User Specialization**: Flexible buyer/seller role management
- **Category Hierarchy**: Scalable product categorization
- **Order Management**: Comprehensive transaction tracking
- **Review System**: Dual rating system for products and sellers

## 📝 Documentation

- **ER Diagram**: Visual representation of entity relationships
- **Relational Schema**: Detailed table structure and constraints
- **Functional Dependencies**: Complete FD analysis and minimal sets
- **Sample Data**: Realistic test data for system validation
- **Query Examples**: Common operations and use cases

## 🔧 Future Enhancements

- **Advanced Search**: Full-text search capabilities
- **Recommendation System**: Product recommendation algorithms
- **Analytics Dashboard**: Business intelligence features
- **Mobile API**: REST API for mobile applications
- **Real-time Notifications**: Order status updates
- **Multi-language Support**: Internationalization features

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 Team

**Team ID**: T612  
**Project Name**: E-commerce Database Management System  
**Course**: Database Management Systems

## 📞 Contact

For questions or suggestions, please open an issue or contact the development team.

---

**Note**: This project is developed for educational purposes as part of a Database Management Systems course. The design demonstrates industry-standard database practices and can be extended for real-world applications.

## 🔗 Quick Links

- [View ER Diagram](DBMS_Project_ER_Diagram.pdf)
- [Database Schema](DBMS_Project_Relational_Schema.pdf)
- [Normalization Analysis](DBMS_Project_FDs_and_BCNF.pdf)
- [Sample Queries](Sample_Queries.sql)
- [Database Setup](DDL_Script.sql)
