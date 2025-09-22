# 🚀 Customer Relationship Management (CRM) System

[![PHP](https://img.shields.io/badge/PHP-7.4%2B-blue.svg)](https://php.net)
[![MySQL](https://img.shields.io/badge/MySQL-8.0%2B-orange.svg)](https://mysql.com)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26.svg)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6.svg)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E.svg)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

A comprehensive, full-stack Customer Relationship Management (CRM) system designed and engineered from the ground up. This project showcases a complete enterprise-grade solution with modern UI design, robust front-end development, and scalable back-end architecture with a well-structured MySQL database.

## 📋 Table of Contents

- [✨ Features](#-features)
- [🏗️ System Architecture](#️-system-architecture)
- [💻 Tech Stack](#-tech-stack)
- [📊 Database Schema](#-database-schema)
- [🚀 Installation](#-installation)
- [⚙️ Configuration](#️-configuration)
- [📖 Usage Guide](#-usage-guide)
- [👥 User Roles](#-user-roles)
- [🔧 Development](#-development)
- [📚 Documentation](#-documentation)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)

## ✨ Features

### 🎯 Core CRM Functionality
- **Customer Management**: Complete customer lifecycle management with detailed profiles
- **Lead Management**: Track and nurture leads through the sales pipeline
- **Interaction Tracking**: Log and monitor all customer communications and touchpoints
- **Reminder System**: Automated reminders with notifications for follow-ups and important events
- **Search & Filter**: Advanced search capabilities across all entities
- **Role-Based Access Control**: Secure multi-level user management

### 🔐 Security & Authentication
- **Secure Login System**: Session-based authentication with role verification
- **User Verification**: Multi-step verification process for new users
- **Access Control**: Granular permissions based on user roles
- **SQL Injection Protection**: Prepared statements throughout the application

### 📱 User Interface
- **Responsive Design**: Mobile-first approach with modern CSS3
- **Interactive Dashboard**: Real-time overview of CRM metrics and activities
- **Intuitive Navigation**: User-friendly sidebar navigation with quick access
- **Dynamic Content**: AJAX-powered updates for seamless user experience
- **Multi-language Support**: Internationalization ready (English/German)

### 📈 Advanced Features
- **Entity Management**: CRUD operations for all CRM entities
- **Data Export/Import**: Database management and backup capabilities
- **Search Functionality**: Global search across customers, leads, and interactions
- **Reminder Notifications**: Visual indicators and count badges for pending tasks
- **Settings Management**: Customizable system preferences

## 📸 Screenshots

### 🔐 Login Interface
The system features a clean, professional login interface with multi-language support and secure authentication.

### 📊 Admin Dashboard
Comprehensive dashboard showing all CRM entities with advanced filtering and search capabilities.

### 👤 User Management
Role-based access control with different views for Administrators and Sales Representatives.

### 📋 Customer Management
Intuitive customer management interface with detailed profiles and interaction history.

### ⏰ Reminder System
Smart reminder system with visual notifications and automatic past-due marking.

*Note: Screenshots can be added by placing image files in a `/docs/images/` directory and linking them here.*

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    Frontend Layer                           │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐        │
│  │   HTML5     │  │    CSS3     │  │ JavaScript  │        │
│  │             │  │  Responsive │  │    AJAX     │        │
│  └─────────────┘  └─────────────┘  └─────────────┘        │
└─────────────────────────────────────────────────────────────┘
                              │
┌─────────────────────────────────────────────────────────────┐
│                 Application Layer (PHP)                     │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐        │
│  │ Session Mgmt│  │ Auth System │  │  Business   │        │
│  │             │  │             │  │   Logic     │        │
│  └─────────────┘  └─────────────┘  └─────────────┘        │
└─────────────────────────────────────────────────────────────┘
                              │
┌─────────────────────────────────────────────────────────────┐
│                  Database Layer                             │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐        │
│  │   MySQL     │  │ Prepared    │  │ Relational  │        │
│  │  Database   │  │ Statements  │  │   Schema    │        │
│  └─────────────┘  └─────────────┘  └─────────────┘        │
└─────────────────────────────────────────────────────────────┘
```

## 💻 Tech Stack

### Backend
- **PHP 7.4+**: Server-side scripting and business logic
- **MySQL 8.0+**: Relational database management
- **Apache/Nginx**: Web server
- **XAMPP**: Local development environment

### Frontend
- **HTML5**: Semantic markup and structure
- **CSS3**: Modern styling with animations and responsive design
- **JavaScript**: Client-side interactivity and AJAX

### Development Tools
- **phpMyAdmin**: Database administration
- **Git**: Version control
- **Visual Studio Code**: Development environment

## 📊 Database Schema

The CRM system uses a normalized MySQL database with the following key tables:

### 🏢 Core Entities

#### **Staff Table**
```sql
CREATE TABLE staff (
    Staff_ID INT PRIMARY KEY AUTO_INCREMENT,
    Role_ID INT NOT NULL,
    Username VARCHAR(50) NOT NULL,
    Password VARCHAR(50) NOT NULL,
    Email VARCHAR(50),
    First_Name VARCHAR(50) NOT NULL,
    Last_Name VARCHAR(50) NOT NULL,
    Address VARCHAR(50),
    FOREIGN KEY (Role_ID) REFERENCES role(Role_ID)
);
```

#### **Customer Table**
```sql
CREATE TABLE customer (
    Customer_ID INT PRIMARY KEY AUTO_INCREMENT,
    Last_Name VARCHAR(50) NOT NULL,
    First_Name VARCHAR(50) NOT NULL,
    Email VARCHAR(50),
    Address VARCHAR(50),
    Company VARCHAR(50) NOT NULL,
    Phone_Number VARCHAR(20),
    Staff_ID INT,
    FOREIGN KEY (Staff_ID) REFERENCES staff(Staff_ID)
);
```

#### **Lead Table**
```sql
CREATE TABLE lead (
    Lead_ID INT PRIMARY KEY AUTO_INCREMENT,
    Last_Name VARCHAR(50) NOT NULL,
    First_Name VARCHAR(50) NOT NULL,
    Email VARCHAR(50),
    Address VARCHAR(50),
    Company VARCHAR(50) NOT NULL,
    Phone_Number VARCHAR(20),
    Staff_ID INT,
    FOREIGN KEY (Staff_ID) REFERENCES staff(Staff_ID)
);
```

### 📞 Interaction Management

#### **Interaction Table**
```sql
CREATE TABLE interaction (
    Interaction_ID INT PRIMARY KEY AUTO_INCREMENT,
    Interaction_Type VARCHAR(30) NOT NULL,
    Description VARCHAR(50),
    Interaction_Date DATE NOT NULL,
    Staff_ID INT,
    Customer_ID INT,
    Lead_ID INT,
    FOREIGN KEY (Staff_ID) REFERENCES staff(Staff_ID),
    FOREIGN KEY (Customer_ID) REFERENCES customer(Customer_ID),
    FOREIGN KEY (Lead_ID) REFERENCES lead(Lead_ID)
);
```

### ⏰ Reminder System

#### **Reminder Record Table**
```sql
CREATE TABLE reminder_record (
    Reminder_Record_ID INT PRIMARY KEY AUTO_INCREMENT,
    Event_Date DATE NOT NULL,
    Reminder_ID INT,
    Lead_ID INT,
    Customer_ID INT,
    Description TEXT,
    Staff_ID INT,
    reminder_date DATETIME,
    Event_Time TIME,
    FOREIGN KEY (Reminder_ID) REFERENCES reminder(Reminder_ID),
    FOREIGN KEY (Lead_ID) REFERENCES lead(Lead_ID),
    FOREIGN KEY (Customer_ID) REFERENCES customer(Customer_ID),
    FOREIGN KEY (Staff_ID) REFERENCES staff(Staff_ID)
);
```

### 👥 User Roles
```sql
CREATE TABLE role (
    Role_ID INT PRIMARY KEY AUTO_INCREMENT,
    Role_Title VARCHAR(20) NOT NULL
);

INSERT INTO role VALUES 
(1, 'Admin'),
(2, 'Sales Representative');
```

## 🚀 Installation

### Prerequisites
- **XAMPP/WAMP/LAMP Stack**: PHP 7.4+, MySQL 8.0+, Apache
- **Web Browser**: Modern browser with JavaScript enabled
- **Git**: For cloning the repository

### Step-by-Step Installation

1. **Clone the Repository**
   ```bash
   git clone https://github.com/VanVan120/Customer-Relationship-Management-CRM-System.git
   cd Customer-Relationship-Management-CRM-System
   ```

2. **Extract Source Files**
   ```bash
   # Extract the main project files
   unzip Customer-Relationship-Management-System-main.zip
   cd Customer-Relationship-Management-System-main/COMP1044_CW_G1/COMP1044_CW_G1/COMP1044_SRC/COMP1044_SRC
   ```

3. **Setup Web Server**
   ```bash
   # Copy files to your web server directory
   # For XAMPP:
   cp -r * /opt/lampp/htdocs/crm-system/
   
   # For WAMP:
   cp -r * C:/wamp64/www/crm-system/
   ```

4. **Start Services**
   ```bash
   # Start Apache and MySQL services
   # XAMPP:
   sudo /opt/lampp/lampp start
   
   # Or use XAMPP Control Panel on Windows
   ```

5. **Create Database**
   - Open phpMyAdmin: `http://localhost/phpmyadmin`
   - Create new database: `comp1044_database`
   - Import SQL file: `Customer-Relationship-Management-System-main/COMP1044_CW_G1/COMP1044_CW_G1/comp1044_database.sql`

6. **Access the Application**
   ```
   http://localhost/crm-system/index.php
   ```

## ⚙️ Configuration

### Database Configuration

Update database connection settings in PHP files if needed:

```php
// Database connection settings
$servername = "localhost";
$username = "root";           // Default XAMPP username
$password = "";               // Default XAMPP password (empty)
$dbname = "comp1044_database"; // Database name
```

### Default User Accounts

The system comes with pre-configured user accounts (example):

| Username | Password | Role | Email |
|----------|----------|------|--------|
| Admin 1 | 123 | Admin | ivan@gmail.com |
| Admin 2 | 123 | Admin | cham@gmail.com |
| Admin 3 | 123 | Admin | felimy@gmail.com |
| SalesRep 1 | 123 | Sales Representative | ngys@gmail.com |
| SalesRep 2 | 123 | Sales Representative | pius@gmail.com |

⚠️ **Security Note**: Change default passwords in production environment!

## 📖 Usage Guide

### 🔐 Login Process

1. Navigate to the application URL
2. Enter your username and password
3. System validates credentials and establishes session
4. Redirected to dashboard based on user role

### 🏠 Dashboard Overview

**Admin Dashboard**:
- View all customers and leads
- Access all system functions
- Manage users and permissions
- System-wide analytics

**Sales Representative Dashboard**:
- View assigned customers and leads
- Personal interaction history
- Individual reminders and tasks

### 📋 Managing Entities

#### Customer Management
- **Add New Customer**: Fill customer details form
- **View Customers**: Browse paginated customer list
- **Edit Customer**: Update customer information
- **Delete Customer**: Remove customer record
- **Search Customers**: Filter by name, company, or email

#### Lead Management
- **Lead Capture**: Add potential customers
- **Lead Nurturing**: Track communication history
- **Lead Conversion**: Convert leads to customers
- **Lead Analytics**: Monitor conversion rates

#### Interaction Tracking
- **Log Interactions**: Record calls, meetings, emails
- **Interaction History**: View chronological communication
- **Follow-up Tracking**: Monitor pending actions
- **Interaction Analytics**: Analyze communication patterns

### ⏰ Reminder System

- **Create Reminders**: Set follow-up tasks
- **Reminder Notifications**: Visual indicators in sidebar
- **Mark as Read**: Update reminder status
- **Reminder Search**: Find specific reminders
- **Auto-Mark Past Due**: Automatically mark overdue reminders

## 👥 User Roles

### 🔑 Administrator
**Full System Access**
- User management and role assignment
- View all customers, leads, and interactions
- System configuration and settings
- Database management and maintenance
- Analytics and reporting across all data

**Key Features**:
- Complete CRUD operations on all entities
- User account management
- System-wide search and filtering
- All reminders visibility
- Administrative settings access

### 👤 Sales Representative
**Limited Access Based on Assignment**
- Manage assigned customers and leads
- Log personal interactions
- View and manage personal reminders
- Access to search within assigned entities

### 👤 Sales Representative
**Limited Access Based on Assignment**
- Manage assigned customers and leads
- Log personal interactions
- View and manage personal reminders
- Access to search within assigned entities

**Key Features**:
- Customer/lead assignment based access
- Personal interaction logging
- Individual reminder management
- Limited search scope
- Profile management

## 🔧 Development

### 📁 Project Structure

```
Customer-Relationship-Management-CRM-System/
├── Customer-Relationship-Management-System-main/
│   └── COMP1044_CW_G1/
│       └── COMP1044_CW_G1/
│           ├── COMP1044_SRC/
│           │   └── COMP1044_SRC/          # Main application files
│           │       ├── index.php          # Landing page with language selection
│           │       ├── LoginPage.php      # Authentication system
│           │       ├── HomePage.php       # Main dashboard
│           │       ├── CustomerPage.php   # Customer management
│           │       ├── LeadPage.php       # Lead management
│           │       ├── Interactions.php   # Interaction logging
│           │       ├── ReminderPage.php   # Reminder system
│           │       ├── ManageEntity.php   # CRUD operations
│           │       ├── Search*.php        # Search functionality
│           │       ├── Settings.php       # System configuration
│           │       ├── sidebar.php        # Navigation component
│           │       ├── Style.css          # Main stylesheet
│           │       ├── home.css          # Dashboard specific styles
│           │       ├── verification.css   # Authentication styles
│           │       └── script.js         # JavaScript functionality
│           ├── comp1044_database.sql      # Database schema and data
│           ├── COMP1044_ERD.pdf          # Entity Relationship Diagram
│           ├── COMP1044_WBS.pdf          # Work Breakdown Structure
│           └── COMP1044_SRC.zip          # Source code archive
├── README.md                             # Project documentation
└── LICENSE                              # MIT License
```

### 🎨 Frontend Architecture

**CSS Framework**: Custom responsive design system
- **Style.css**: Global styles and layout framework
- **home.css**: Dashboard-specific styling
- **verification.css**: Authentication page styles

**JavaScript Features**:
- AJAX for dynamic content updates
- Form validation and user feedback
- Interactive UI components
- Session management helpers

**PHP Architecture**:
- **Session-based Authentication**: Secure user management
- **Prepared Statements**: SQL injection prevention
- **Modular Design**: Reusable components and functions
- **Role-based Access Control**: Granular permission system

### 🔒 Security Features

1. **Authentication & Authorization**
   - Session-based login system
   - Password verification
   - Role-based access control
   - Automatic logout on inactivity

2. **Database Security**
   - Prepared statements for all queries
   - Input sanitization
   - SQL injection prevention
   - Connection security

3. **Data Protection**
   - Secure session handling
   - User input validation
   - Error message sanitization
   - Access logging

### 🧪 Testing & Quality Assurance

**Manual Testing Checklist**:
- ✅ User authentication flow
- ✅ CRUD operations for all entities
- ✅ Role-based access verification
- ✅ Search functionality validation
- ✅ Reminder system testing
- ✅ Cross-browser compatibility
- ✅ Mobile responsiveness

**Database Integrity**:
- Foreign key constraints
- Data validation rules
- Backup and recovery procedures
- Performance optimization

## 📚 Documentation

### 📊 Available Documentation
- **Entity Relationship Diagram (ERD)**: Database design and relationships
- **Work Breakdown Structure (WBS)**: Project planning and task breakdown
- **Source Code**: Well-commented PHP, HTML, CSS, and JavaScript files
- **Database Schema**: Complete SQL structure with sample data

### 🔍 Code Examples

#### Customer Search Function
```php
// Search customers by name or company
$searchTerm = $_GET['search'] ?? '';
$sql = "SELECT * FROM customer WHERE 
        First_Name LIKE ? OR Last_Name LIKE ? OR Company LIKE ?";
$stmt = $conn->prepare($sql);
$searchParam = "%{$searchTerm}%";
$stmt->bind_param("sss", $searchParam, $searchParam, $searchParam);
```

#### AJAX Reminder Update
```javascript
// Mark reminder as read via AJAX
function markReminderRead(recordId) {
    fetch('markReminderReadAjax.php', {
        method: 'POST',
        headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
        body: 'record_id=' + recordId
    })
    .then(response => response.text())
    .then(data => {
        if(data === 'success') {
            location.reload(); // Refresh to update counts
        }
    });
}
```

### 📈 Performance Considerations

- **Database Indexing**: Optimized queries with proper indexing
- **Pagination**: Large datasets handled with pagination
- **Caching**: Session-based caching for user data
- **Optimized Queries**: Efficient SQL with prepared statements

## 🚀 Deployment

### Production Deployment Steps

1. **Server Requirements**
   - Linux/Windows Server with Apache/Nginx
   - PHP 7.4+ with MySQL extension
   - MySQL 8.0+ or MariaDB 10.4+
   - SSL certificate for HTTPS

2. **Security Hardening**
   ```php
   // Update default passwords
   // Enable HTTPS only
   // Configure file permissions
   // Set up regular backups
   ```

3. **Performance Optimization**
   - Enable PHP OPcache
   - Configure MySQL query cache
   - Implement CDN for static assets
   - Set up monitoring and logging

### 🔧 Environment Variables
```env
DB_HOST=localhost
DB_USER=your_db_user
DB_PASS=your_secure_password
DB_NAME=comp1044_database
SESSION_LIFETIME=3600
```

## 🤝 Contributing

We welcome contributions to improve the CRM system! Here's how you can contribute:

### 📝 Contribution Guidelines

1. **Fork the Repository**
   ```bash
   git fork https://github.com/VanVan120/Customer-Relationship-Management-CRM-System
   ```

2. **Create Feature Branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

3. **Make Changes**
   - Follow existing code style
   - Add comments for complex logic
   - Test thoroughly before committing

4. **Submit Pull Request**
   - Provide clear description of changes
   - Include screenshots for UI changes
   - Reference any related issues

### 🐛 Bug Reports

When reporting bugs, please include:
- Steps to reproduce the issue
- Expected vs actual behavior
- Browser and version information
- Screenshots if applicable

### 💡 Feature Requests

For new features:
- Describe the use case clearly
- Explain the business value
- Provide mockups if applicable
- Consider implementation complexity

## 🔄 Roadmap

### 🎯 Planned Features
- [ ] **Email Integration**: Direct email sending from the system
- [ ] **Advanced Reporting**: Customizable analytics dashboard
- [ ] **API Development**: RESTful API for third-party integrations
- [ ] **Mobile App**: React Native mobile application
- [ ] **Document Management**: File upload and document tracking
- [ ] **Calendar Integration**: Appointment scheduling system
- [ ] **Advanced Search**: Full-text search with filters
- [ ] **Data Import/Export**: CSV/Excel import/export functionality

### 🔧 Technical Improvements
- [ ] **Framework Migration**: Consider Laravel or CodeIgniter migration
- [ ] **Frontend Framework**: Vue.js or React implementation
- [ ] **Database Optimization**: Query optimization and indexing
- [ ] **Caching Layer**: Redis or Memcached implementation
- [ ] **Unit Testing**: PHPUnit test suite development
- [ ] **Docker Support**: Containerized deployment option

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2025 VanVan120

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

## 🙏 Acknowledgments

- **Development Team**: COMP1044 CW G1 Team Members
- **Educational Institution**: University of Nottingham Malaysia
- **Open Source Community**: For tools and inspiration
- **Beta Testers**: For feedback and bug reports

## 📞 Support & Contact

### 🆘 Getting Help
- **Documentation**: Check this README and code comments
- **Issues**: Create GitHub issue for bugs or features
- **Discussions**: Use GitHub discussions for questions

### 📬 Contact Information
- **Project Repository**: [GitHub](https://github.com/VanVan120/Customer-Relationship-Management-CRM-System)
- **Issue Tracker**: [GitHub Issues](https://github.com/VanVan120/Customer-Relationship-Management-CRM-System/issues)

---

<div align="center">

**⭐ Star this repository if you find it helpful!**

Built with ❤️ by the development team • [View Live Demo](https://your-demo-url.com) • [Report Bug](https://github.com/VanVan120/Customer-Relationship-Management-CRM-System/issues)

</div>
