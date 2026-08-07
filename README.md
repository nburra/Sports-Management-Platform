# Sports Management Platform

A full-stack sports management platform designed to streamline athletic program operations through role-based workflows, centralized data management, and RESTful APIs.

Built using **Python, Flask, MySQL, Streamlit, Docker, and REST APIs**, the application enables coaches, athletes, recruiters, and athletic directors to efficiently manage teams, schedules, recruiting activities, and player performance.

---

# Business Problem

Managing athletic programs often requires coaches, recruiters, athletes, and administrators to coordinate information across multiple disconnected systems.

Common challenges include:

- Fragmented athlete and team information
- Inefficient recruiting workflows
- Manual schedule management
- Limited visibility into player performance
- Duplicate data entry across users

This project demonstrates how a centralized information system can improve operational efficiency by integrating all stakeholders into a single platform.

---

# Solution

Developed a role-based sports management platform that combines a relational database, REST API, and interactive web interface.

The platform enables users to:

- Manage teams and rosters
- Track athlete statistics
- Schedule games and practices
- Coordinate recruiting events
- Search athletes using multiple criteria
- Maintain centralized program information

---

# System Architecture

```
             Users
────────────────────────────────────
 Coaches • Athletes • Recruiters •
 Athletic Directors
────────────────────────────────────
              │
              ▼
      Streamlit Frontend
              │
         REST API Calls
              │
              ▼
          Flask API
      (Business Logic)
              │
         SQL Queries
              │
              ▼
         MySQL Database
```

Docker Compose orchestrates the frontend, backend, and database services for consistent local deployment.

---

# Key Features

## Role-Based Access

The application supports multiple user roles with customized functionality.

### Coach

- View team schedules
- Access team strategies
- Monitor player performance

### Athlete

- View personal statistics
- Track recruiting opportunities
- Access schedules

### Recruiter

- Search athletes by GPA, position, location, and performance
- View player profiles
- Schedule recruiting events

### Athletic Director

- Manage teams
- Schedule practices
- Oversee athletic operations

---

# Database Design

The platform is powered by a normalized relational database containing 13 interconnected tables.

Core entities include:

- Users
- Athletes
- Coaches
- Teams
- Athlete Statistics
- Practices
- Games
- Recruiting Events
- Schools of Interest

The schema utilizes:

- Primary and foreign keys
- Junction tables
- Referential integrity
- Many-to-many relationships
- Parameterized SQL queries

---

# REST API

The backend exposes RESTful endpoints that allow the frontend to interact with the database.

Example capabilities include:

- Retrieve athlete information
- Search players by multiple filters
- Update statistics
- Schedule practices
- Manage recruiting events
- View calendars
- Manage rosters

Business logic is separated from presentation through modular Flask Blueprints.

---

# Technologies

## Programming

- Python

## Backend

- Flask
- Flask-Login
- REST APIs

## Database

- MySQL
- SQL
- Relational Database Design

## Frontend

- Streamlit
- Pandas

## DevOps

- Docker
- Docker Compose

---

# Repository Structure

```
Sports-Management-App/

│
├── api/
│
├── app/
│
├── database-files/
│
├── docker-compose.yaml
│
└── README.md
```

---

# Application Workflow

```
User Login
      │
      ▼
Role Authentication
      │
      ▼
Role-Specific Dashboard
      │
      ▼
REST API Request
      │
      ▼
Flask Business Logic
      │
      ▼
MySQL Database
      │
      ▼
Updated Dashboard
```

---

# Skills Demonstrated

- Business Systems Analysis
- Relational Database Design
- REST API Development
- Full-Stack Application Development
- Process Modeling
- User Workflow Design

---

# Future Improvements

Potential enhancements include:

- Authentication using OAuth
- Cloud deployment (AWS or Azure)
- Real-time notifications
- Team messaging
- Mobile-responsive interface
- Analytics dashboards for recruiting and player performance
- AI-powered athlete matching and recruiting recommendations

---
