# UniPulse - Smart Campus Management System

![UniPulse](https://img.shields.io/badge/Version-1.0.0-blue) ![TypeScript](https://img.shields.io/badge/Frontend-TypeScript-3178C6) ![Java](https://img.shields.io/badge/Backend-Java-ED8B00) ![React](https://img.shields.io/badge/UI-React-61DAFB) ![Spring Boot](https://img.shields.io/badge/Framework-Spring%20Boot-6DB33F)

UniPulse is a comprehensive smart campus management system designed to streamline facility management, resource reservation, maintenance ticket tracking, and administrative operations for educational institutions. The system provides an intuitive interface for students, technicians, and administrators to collaborate efficiently.

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Project Architecture](#-project-architecture)
- [Technology Stack](#-technology-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [API Endpoints](#-api-endpoints)
- [Database Schema](#-database-schema)
- [Key Components](#-key-components)
- [Contributing](#-contributing)

---

## 🎯 Overview

UniPulse is built with a **modern, scalable architecture** separating concerns between frontend and backend services. It addresses the critical needs of campus facilities management including:

- **Resource Management**: Track and manage lecture halls, labs, meeting rooms, and equipment
- **Reservation System**: Book campus resources with an intuitive reservation interface
- **Maintenance Tickets**: Report and track facility issues with prioritization and assignment
- **User Management**: Role-based access control (Student, Technician, Admin)
- **Analytics & Reporting**: Dashboard with key performance indicators and usage analytics
- **Real-time Notifications**: Keep users informed about reservation and ticket updates

---

## ✨ Features

### 📚 Resource Management
- **CRUD Operations**: Create, read, update, delete campus resources
- **Resource Types**: Support for Lecture Halls, Labs, Meeting Rooms, and Equipment
- **Status Tracking**: Active/Out-of-Service status management
- **Advanced Search**: Filter resources by type, status, location, and capacity
- **Availability Windows**: Set availability schedules for resources

### 🗓️ Reservation System
- **Easy Booking**: Intuitive calendar-based reservation interface
- **User Dashboard**: View personal reservations with status tracking
- **Admin Approval**: Review and approve/reject reservation requests
- **Conflict Detection**: Prevent double-booking of resources
- **Notifications**: Real-time alerts for reservation status changes

### 🔧 Maintenance & Ticket Management
- **Ticket Creation**: Report facility issues with attachments
- **Priority Levels**: Categorize tickets as Low, Medium, High, or Critical
- **Status Workflow**: OPEN → IN_PROGRESS → RESOLVED → CLOSED
- **Technician Assignment**: Route tickets to appropriate maintenance staff
- **Comments & Messaging**: Real-time communication between users and technicians
- **Attachment Support**: Upload evidence, photos, or documentation
- **Resolution Notes**: Document resolution details and findings

### 👥 User Management
- **Role-Based Access**: Three-tier system (Student, Technician, Admin)
- **Authentication**: Secure login with JWT tokens
- **OAuth Integration**: Google OAuth support for streamlined access
- **Profile Management**: Complete user profiles with profile images
- **Role Request System**: Process requests for role elevation

### 📊 Analytics & Dashboard
- **KPI Metrics**: Track overall system performance
- **Time-Based Analytics**: Daily, weekly, monthly, and yearly reports
- **Resource Utilization**: Analyze resource usage patterns
- **Category Analytics**: Break down tickets by category
- **Custom Date Ranges**: Generate reports for specific periods

---

## 🏗️ Project Architecture

UniPulse follows a **3-tier architecture** pattern:

```
┌─────────────────────────────────────────────────────────────┐
│                     PRESENTATION LAYER                      │
│           Frontend (React + TypeScript + Vite)              │
│                   (Port: 5173/5174)                         │
└─────────────────┬───────────────────────────────────────────┘
                  │ REST API (HTTP/JSON)
┌─────────────────▼───────────────────────────────────────────┐
│                  APPLICATION LAYER                          │
│    Backend (Spring Boot + Java 17)                          │
│                   (Port: 8083)                              │
├─────────────────────────────────────────────────────────────┤
│  Controllers │ Services │ Repositories │ DTOs │ Entities    │
│  (REST API)  │(Business)│ (Data Access)│(API) │(Models)     │
└─────────────────┬───────────────────────────────────────────┘
                  │ JDBC
┌─────────────────▼───────────────────────────────────────────┐
│                    DATA LAYER                               │
│              MySQL Database (8.0+)                          │
│                  (Port: 3306)                               │
└─────────────────────────────────────────────────────────────┘
```

### Architecture Benefits:
- **Separation of Concerns**: Clear boundaries between UI, business logic, and data
- **Scalability**: Easy to scale frontend and backend independently
- **Maintainability**: Modular structure simplifies debugging and updates
- **Reusability**: Shared DTOs and services across multiple endpoints
- **Security**: Centralized authentication and authorization handling

---

## 🛠️ Technology Stack

### Frontend
| Technology | Purpose | Version |
|-----------|---------|---------|
| **React** | UI Library | 19.2.0 |
| **TypeScript** | Type-Safe JavaScript | 5.9.3 |
| **Vite** | Build Tool & Dev Server | 7.3.2 |
| **React Router** | Client-Side Routing | 7.13.2 |
| **TailwindCSS** | Styling Framework | 4.2.2 |
| **React Hook Form** | Form Management | 7.72.0 |
| **Zod** | Schema Validation | 4.3.6 |
| **Axios** | HTTP Client | 1.15.1 |
| **Framer Motion** | Animations | 12.38.0 |
| **Recharts** | Data Visualization | 3.8.1 |
| **Lucide React** | Icon Library | 1.7.0 |

### Backend
| Technology | Purpose | Version |
|-----------|---------|---------|
| **Spring Boot** | Framework | 4.0.5 |
| **Java** | Programming Language | 17 |
| **Spring Data JPA** | ORM & Persistence | Latest |
| **Spring Security** | Authentication & Authorization | Latest |
| **JWT** | Token-Based Auth | 0.13.0 |
| **MySQL Connector** | Database Driver | Latest |
| **Lombok** | Code Generation | Latest |
| **Maven** | Build Tool | 3.9+ |

---

## 📂 Project Structure

```
UniPulse/
├── frontend/                          # React Frontend Application
│   ├── src/
│   │   ├── components/               # Reusable React Components
│   │   ├── pages/                    # Page Components
│   │   ├── services/                 # API Service Layer (Axios)
│   │   ├── hooks/                    # Custom React Hooks
│   │   ├── types/                    # TypeScript Interfaces
│   │   ├── App.tsx                   # Main App Component
│   │   └── main.tsx                  # Entry Point
│   ├── package.json                  # Frontend Dependencies
│   ├── vite.config.ts                # Vite Configuration
│   └── tsconfig.json                 # TypeScript Configuration
│
├── backend/                           # Spring Boot Backend
│   ├── src/main/java/com/unipulse/backend/
│   │   ├── controller/               # REST Controllers (API Endpoints)
│   │   ├── service/                  # Business Logic (Services)
│   │   ├── repository/               # Database Access (Repositories)
│   │   ├── model/                    # Entity Classes (JPA)
│   │   ├── entity/                   # Additional Entity Models
│   │   ├── dto/                      # Data Transfer Objects
│   │   ├── enums/                    # Enumeration Classes
│   │   ├── security/                 # Security Configuration
│   │   ├── exception/                # Exception Handling
│   │   ├── util/                     # Utility Classes
│   │   └── BackendApplication.java   # Spring Boot Main Class
│   ├── src/main/resources/
│   │   └── application.properties    # Application Configuration
│   ├── pom.xml                       # Maven Dependencies
│   ├── SETUP_INSTRUCTIONS.md         # Setup Guide
│   └── database-setup.sql            # Database Initialization
│
├── README.md                          # Project Documentation
├── TECHNICIAN_STATUS_UPDATE_INSTRUCTIONS.md
├── package-lock.json                 # Dependency Lock File
└── .gitignore                        # Git Ignore Rules
```

---

## 🚀 Getting Started

### Prerequisites

Ensure you have the following installed:

- **Node.js** (v18+) & **npm** (v9+)
- **Java JDK** (v17+)
- **Maven** (v3.9+)
- **MySQL Server** (v8.0+)
- **Git**

### Backend Setup

#### 1. Create Database

```bash
# Open MySQL and create the database
mysql -u root -p

# In MySQL prompt:
CREATE DATABASE IF NOT EXISTS unipulse;
EXIT;
```

Or use the provided script:
```bash
mysql -u root -p < backend/database-setup.sql
```

#### 2. Configure Backend

Create `backend/src/main/resources/application.properties`:

```properties
# Application
spring.application.name=backend
server.port=8083

# Database Configuration
spring.datasource.url=jdbc:mysql://localhost:3306/unipulse?createDatabaseIfNotExist=true&useSSL=false&serverTimezone=UTC&allowPublicKeyRetrieval=true
spring.datasource.username=root
spring.datasource.password=root1234
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# JPA/Hibernate
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect
spring.jpa.properties.hibernate.format_sql=true

# Logging
logging.level.org.hibernate.SQL=DEBUG
```

#### 3. Build and Run Backend

```bash
# Navigate to backend directory
cd backend

# Build the project
./mvnw clean package -DskipTests

# Run the application
./mvnw spring-boot:run
```

The backend will be available at `http://localhost:8083`

### Frontend Setup

#### 1. Install Dependencies

```bash
# Navigate to frontend directory
cd frontend

# Install all dependencies
npm install
```

#### 2. Run Development Server

```bash
# Start Vite dev server
npm run dev

# Or start with multiple ports
npm start
```

The frontend will be available at `http://localhost:5174` (and admin at `http://localhost:5174/admin/login`)

### Verify Installation

#### Backend Test:
```bash
# Get all resources
curl http://localhost:8083/api/resources

# Create a test resource
curl -X POST http://localhost:8083/api/resources \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Test Lecture Hall",
    "type": "LECTURE_HALL",
    "capacity": 100,
    "location": "Building 1, Floor 2",
    "description": "A test lecture hall",
    "availabilityWindows": "Mon-Fri 8AM-6PM",
    "status": "ACTIVE"
  }'
```

#### Frontend Test:
- Open browser to `http://localhost:5174`
- Navigate to facilities/resources page
- Should see resources from backend API

---

## 📡 API Endpoints

### Authentication Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | User registration |
| POST | `/api/auth/login` | User login |
| POST | `/api/auth/admin/register` | Admin registration |
| POST | `/api/auth/admin/login` | Admin login |
| PUT | `/api/auth/complete-profile` | Complete user profile |
| GET | `/api/auth/google/login/start` | Google OAuth login |

### Resource Management

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/resources` | Get all resources |
| GET | `/api/resources/{id}` | Get resource by ID |
| POST | `/api/resources` | Create new resource |
| PUT | `/api/resources/{id}` | Update resource |
| DELETE | `/api/resources/{id}` | Delete resource |
| PATCH | `/api/resources/{id}/status` | Update resource status |
| GET | `/api/resources/type/{type}` | Get resources by type |
| GET | `/api/resources/status/{status}` | Get resources by status |
| GET | `/api/resources/search` | Search resources with filters |

### Reservation Management

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/reservations` | Create reservation |
| GET | `/api/reservations` | Get all reservations (Admin) |
| GET | `/api/reservations/{id}` | Get reservation by ID |
| GET | `/api/reservations/user/{userId}` | Get user's reservations |
| GET | `/api/reservations/summary/{userId}` | Get user dashboard summary |
| PUT | `/api/reservations/{id}/status` | Update reservation status |
| DELETE | `/api/reservations/{id}` | Cancel reservation |
| GET | `/api/reservations/calendar` | Calendar date-range query |

### Ticket Management

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/tickets` | Get all tickets |
| GET | `/api/tickets/{id}` | Get ticket by ID |
| POST | `/api/tickets` | Create ticket (with attachments) |
| PUT | `/api/tickets/{id}` | Update ticket |
| DELETE | `/api/tickets/{id}` | Delete ticket |
| PATCH | `/api/tickets/{id}/status` | Update ticket status |
| PATCH | `/api/tickets/{id}/assign-technician` | Assign technician |
| POST | `/api/tickets/{id}/comments` | Add comment to ticket |
| GET | `/api/tickets/{id}/comments` | Get ticket comments |
| POST | `/api/attachments/{attachmentId}/download` | Download attachment |

### Analytics

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/analytics/overall` | Overall analytics |
| GET | `/api/analytics/today` | Today's analytics |
| GET | `/api/analytics/week` | Week's analytics |
| GET | `/api/analytics/month` | Month's analytics |
| GET | `/api/analytics/year` | Year's analytics |
| GET | `/api/analytics/custom` | Custom date range analytics |
| GET | `/api/analytics/resources` | Resource utilization analytics |
| GET | `/api/analytics/kpi` | Key performance indicators |

### Notifications

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/notifications/user/{userId}` | Get user notifications |
| GET | `/api/notifications/user/{userId}/unread` | Get unread notifications |
| PUT | `/api/notifications/{id}/read` | Mark notification as read |
| PUT | `/api/notifications/user/{userId}/read-all` | Mark all as read |
| GET | `/api/reservation-notifications/user/{userId}` | Get reservation notifications |

---

## 🗄️ Database Schema

### Core Tables

#### Users Table
```sql
CREATE TABLE users (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100),
    sliit_id VARCHAR(50) UNIQUE,
    email VARCHAR(255) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    role ENUM('STUDENT', 'TECHNICIAN', 'ADMIN') NOT NULL,
    provider ENUM('LOCAL', 'GOOGLE') DEFAULT 'LOCAL',
    profile_image LONGTEXT,
    profile_completed BOOLEAN DEFAULT FALSE,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

#### Resources Table
```sql
CREATE TABLE resources (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    type ENUM('LECTURE_HALL', 'LAB', 'MEETING_ROOM', 'EQUIPMENT') NOT NULL,
    capacity INT,
    location VARCHAR(255) NOT NULL,
    description TEXT NOT NULL,
    availability_windows TEXT,
    status ENUM('ACTIVE', 'OUT_OF_SERVICE') NOT NULL,
    image_url VARCHAR(500),
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

#### Reservations Table
```sql
CREATE TABLE reservations (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    user_id VARCHAR(100) NOT NULL,
    user_name VARCHAR(100),
    resource_id BIGINT NOT NULL,
    reservation_date DATE NOT NULL,
    start_time TIME NOT NULL,
    end_time TIME NOT NULL,
    expected_attendees INT,
    purpose TEXT NOT NULL,
    special_notes TEXT,
    status ENUM('PENDING', 'APPROVED', 'REJECTED', 'CANCELLED') DEFAULT 'PENDING',
    admin_reason TEXT,
    reviewed_by VARCHAR(100),
    reviewed_at DATETIME,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (resource_id) REFERENCES resources(id)
);
```

#### Tickets Table
```sql
CREATE TABLE tickets (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    ticket_code VARCHAR(50) UNIQUE NOT NULL,
    category VARCHAR(100) NOT NULL,
    location VARCHAR(255) NOT NULL,
    priority ENUM('LOW', 'MEDIUM', 'HIGH', 'CRITICAL') NOT NULL,
    status ENUM('OPEN', 'IN_PROGRESS', 'RESOLVED', 'CLOSED') NOT NULL DEFAULT 'OPEN',
    description TEXT NOT NULL,
    preferred_contact VARCHAR(255) NOT NULL,
    created_by VARCHAR(150) NOT NULL,
    created_by_user_id BIGINT,
    assigned_technician VARCHAR(150),
    technician_type VARCHAR(100),
    resolution_notes TEXT,
    rejection_reason TEXT,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

#### Ticket Comments Table
```sql
CREATE TABLE ticket_comments (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    ticket_id BIGINT NOT NULL,
    author_name VARCHAR(150) NOT NULL,
    author_role VARCHAR(50) NOT NULL,
    message TEXT NOT NULL,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (ticket_id) REFERENCES tickets(id)
);
```

#### Ticket Attachments Table
```sql
CREATE TABLE ticket_attachments (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    ticket_id BIGINT NOT NULL,
    file_name VARCHAR(255) NOT NULL,
    file_type VARCHAR(100) NOT NULL,
    file_path VARCHAR(500) NOT NULL,
    uploaded_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (ticket_id) REFERENCES tickets(id)
);
```

---

## 🔑 Key Components

### Frontend Components

#### Pages
- **Dashboard**: User overview with statistics and quick actions
- **Resources/Facilities**: Browse and manage campus resources
- **Reservations**: Book and manage facility reservations
- **Tickets**: Create, track, and manage maintenance tickets
- **Admin Panel**: Administrative controls and approvals
- **Analytics**: View system analytics and reports

#### Services
- **ResourceService**: Handle resource-related API calls
- **ReservationService**: Manage reservation operations
- **TicketService**: Ticket CRUD and management
- **AuthService**: Authentication and authorization
- **AnalyticsService**: Fetch analytics data

### Backend Components

#### Controllers
- **ResourceController**: REST endpoints for resource management
- **ReservationController**: Reservation CRUD operations
- **TicketController**: Ticket management and assignment
- **AuthController**: User authentication and registration
- **AnalyticsController**: Analytics and reporting endpoints
- **NotificationController**: Notification management

#### Services
- **ResourceService**: Business logic for resources
- **ReservationService**: Reservation processing and validation
- **TicketService**: Ticket workflow management
- **AuthService**: Authentication and user management
- **AnalyticsService**: Data aggregation and reporting
- **NotificationService**: Notification creation and delivery

#### Repositories
- **ResourceRepository**: Database access for resources
- **ReservationRepository**: Reservation data persistence
- **TicketRepository**: Ticket data access
- **UserRepository**: User data management
- **TicketCommentRepository**: Comment persistence

---

## 📝 Enums & Data Types

### Ticket Status
- `OPEN`: Ticket created, awaiting assignment
- `IN_PROGRESS`: Technician working on the issue
- `RESOLVED`: Issue resolved, awaiting closure confirmation
- `CLOSED`: Ticket completed and closed

### Ticket Priority
- `LOW`: Non-urgent, can wait
- `MEDIUM`: Should be addressed soon
- `HIGH`: Urgent, needs quick attention
- `CRITICAL`: Emergency, requires immediate action

### Resource Status
- `ACTIVE`: Available for reservation
- `OUT_OF_SERVICE`: Not available for reservation

### Resource Type
- `LECTURE_HALL`: Classroom spaces
- `LAB`: Laboratory facilities
- `MEETING_ROOM`: Meeting/conference spaces
- `EQUIPMENT`: Shared equipment

### User Roles
- `STUDENT`: Regular campus user
- `TECHNICIAN`: Maintenance staff
- `ADMIN`: System administrator

### Reservation Status
- `PENDING`: Awaiting admin approval
- `APPROVED`: Reservation confirmed
- `REJECTED`: Request denied by admin
- `CANCELLED`: Cancelled by user

---

## 🔒 Security Features

- **JWT Authentication**: Secure token-based authentication
- **Spring Security**: Role-based access control (RBAC)
- **Password Encryption**: Bcrypt password hashing
- **CORS Configuration**: Cross-origin resource sharing
- **Input Validation**: Data validation at API level
- **Exception Handling**: Centralized error handling

---

## 📖 Additional Resources

- [Backend Setup Instructions](./backend/SETUP_INSTRUCTIONS.md)
- [Technician Status Update Guide](./TECHNICIAN_STATUS_UPDATE_INSTRUCTIONS.md)
- [Database Setup Script](./backend/database-setup.sql)

---

## 🤝 Contributing

Contributions are welcome! Please follow these guidelines:

1. **Fork the repository** and create a feature branch
2. **Make your changes** with clear, descriptive commits
3. **Test thoroughly** before submitting a pull request
4. **Write documentation** for new features
5. **Follow code style** conventions of the project

---

## 📄 License

This project is part of the SLIIT IT3030 - Professional Advanced Framework course (2026, Semester 1).

---

## 📞 Support

For issues, questions, or suggestions, please:

1. Check existing issues and documentation
2. Create a detailed GitHub issue
3. Include relevant error messages and logs

---

## 🙏 Acknowledgments

- **Spring Boot Team** for the excellent framework
- **React Team** for the dynamic UI library
- **SLIIT Faculty** for guidance and support

---

**Last Updated**: May 2026  
**Version**: 1.0.0  
**Status**: Active Development
