# The Royal To-Do List

A sophisticated task management application with mystical twist, featuring curse validation and palindrome detection capabilities. Built with a modern microservices architecture using NestJS backend and Angular frontend.

## 🏗️ Architecture Overview

This application follows a **3-tier microservices architecture** designed for scalability, maintainability, and development efficiency:

### **Frontend Layer**
- **Framework**: Angular 19.2.0 with TypeScript
- **UI Library**: Tailwind CSS + DaisyUI for modern, responsive design
- **Architecture**: Component-based SPA (Single Page Application)
- **Development Server**: Angular CLI dev server with hot reload

### **Backend Layer**
- **Framework**: NestJS (Node.js framework)
- **Language**: TypeScript
- **Architecture**: Modular microservices with dependency injection
- **API**: RESTful APIs with global validation pipes
- **Database ORM**: Prisma with type-safe database operations

### **Database Layer**
- **Database**: MySQL 8.0
- **ORM**: Prisma with automated migrations
- **Features**: Optimized indexes for performance, structured data modeling

### **Key Architectural Decisions**

1. **Containerized Development**: Docker Compose orchestrates all services for consistent development environments
2. **Database-First Approach**: Prisma schema drives the data model with type safety throughout the stack
3. **API-First Design**: Well-defined REST endpoints with comprehensive validation
4. **Hot Reload Development**: Both frontend and backend support live code changes
5. **Microservices Communication**: Container networking enables seamless service-to-service communication

## 🚀 Backend Runtime Justification

### Why NestJS?

**NestJS** was chosen as the backend runtime for several strategic reasons:

1. **TypeScript-First**: Provides end-to-end type safety from database to API responses
2. **Decorator-Based Architecture**: Clean, readable code with dependency injection patterns
3. **Built-in Validation**: Class-validator integration ensures robust input validation
4. **Scalability**: Modular structure supports easy feature expansion and microservices architecture
5. **Developer Experience**: Excellent debugging support and extensive CLI tooling
6. **Performance**: Built on Express.js with optimizations for high-throughput applications
7. **Ecosystem**: Rich ecosystem with seamless integration for databases, testing, and deployment

### Technical Benefits

- **Prisma Integration**: Type-safe database operations with automatic client generation
- **Global Pipes**: Centralized validation and transformation logic
- **CORS Configuration**: Secure cross-origin resource sharing for frontend integration
- **Modular Design**: Feature modules (todos, cron-process) enable clean separation of concerns

## 📋 Prerequisites

Before running the application, ensure you have the following installed:

- **Docker**: Version 20.0 or higher
- **Git**: For cloning the repository

## 🛠️ Local Development Setup

### Step 1: Clone the Repository

This project uses Git submodules for managing the backend and frontend codebases. Clone the repository with submodules:

```bash
git clone https://github.com/julian-guerra92/the-royal-todo-list.git
cd the-royal-todo-list
git submodule update --init --recursive
```

### Step 2: Environment Configuration

1. Copy the environment template:
```bash
cp .env.example .env
```

2. Review and modify the `.env` file if needed:
```env
BACKEND_PORT=3000
FRONTEND_PORT=4200
DATABASE_URL="mysql://root:rootpassword@mysql:3306/royal_tech_db"
```

### Step 3: Build and Start Services

Start all services using Docker Compose:

```bash
# Build and start all services in detached mode
docker-compose up --build -d

# Or start with logs visible (recommended for first run)
docker-compose up --build
```

### Step 4: Verify Installation

1. **Backend API**: Open [http://localhost:3000/api](http://localhost:3000/api)
2. **Frontend Application**: Open [http://localhost:4200](http://localhost:4200)
3. **Database**: MySQL is accessible at `localhost:3306`

### Step 5: Database Initialization

The database is automatically initialized when the backend starts:
- Prisma migrations run automatically via the `docker:start` script
- Database schema is created
- Tables and indexes are configured for optimal performance

## 🔧 Additional Development Commands

### Docker Management
```bash
# Stop all services
docker-compose down

# Rebuild specific service
docker-compose build todo-list-back

# View service logs
docker-compose logs -f [service-name]

# Clean up resources
docker-compose down -v --remove-orphans
```

### Database Operations
```bash
# Reset database (inside backend container)
docker-compose exec todo-list-back npx prisma migrate reset

# Generate Prisma client
docker-compose exec todo-list-back npx prisma generate

# View database schema
docker-compose exec todo-list-back npx prisma db pull
```

## 📡 API Documentation

The application includes a comprehensive Postman collection with all available endpoints, request examples, and response schemas. This collection is located in the next url: [Postman Collection Link](https://documenter.getpostman.com/view/21847342/2sB3QGvCRV)
