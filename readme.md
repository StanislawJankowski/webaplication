# PleaseLetMePass - Digital Asset Management System

PleaseLetMePass is a comprehensive Digital Asset Management (DAM) system designed for organizing, storing, retrieving, and sharing digital educational resources such as images, audio, and video files. The platform aims to centralize digital resources in a structured and intuitive repository, allowing users to efficiently manage, retrieve, and share assets based on metadata, categories, and permissions.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technology Stack](#technology-stack)
- [System Architecture](#system-architecture)
- [API Documentation](#api-documentation)
- [Installation](#installation)
- [Running the Application](#running-the-application)
- [Development](#development)
- [Contributing](#contributing)
- [License](#license)

## Overview

PleaseLetMePass is a non-profit platform focusing on learning, where individuals and institutions can share educational content such as lectures, notes, and podcasts. The system provides a centralized repository for digital assets with advanced organization, search, and access control capabilities.

### User Roles

The system supports various user roles with different permissions:

1. **Administrator** - Full access and control over system settings, user management, and file organization
2. **Managers** - Mostly full access and control over system settings, user management, and file organization
3. **Security Officers** - Access to reported posts to review and handle violations
4. **Verifiers** - Specialists who verify the accuracy of knowledge provided by users
5. **Contributors** - Verified users whose content gets priority in search results
6. **Standard Users** - Can browse, download, use, comment, and add assets
7. **Guests** - Limited access to publicly available assets

## Features

### Core Functionalities

1. **Access Management** - Role-based permissions and access control
2. **Advanced Search and Filtering** - Find learning materials using metadata, tags, and categories
3. **User-friendly File Management** - Intuitive UI for uploading, categorizing, editing, and searching assets
4. **Security and Backup** - Regular backups and comprehensive security measures
5. **Collaboration and Sharing** - Real-time tracking of changes and shared asset management

### Web Pages and Sections

- Homepage with introductions and popular content
- User authentication (login/registration)
- User dashboards and profiles
- Admin panel for system management
- Asset library with search and filtering
- Upload functionality with metadata management
- Reporting system for content moderation

### Special UI Elements

- Drag and drop upload
- Notifications and alerts
- Customizable interface
- Social features (commenting, upvoting)
- Preview functionality for various file types
- Content reporting mechanism
- Two-factor authentication for security

### Data Analysis

- User activity statistics
- Access logs and tracking
- File popularity metrics
- Reports and analytics
- Exportable data for analysis

## Technology Stack

### Backend
- Java 17
- Spring Boot 3.1.x
- Spring Security with JWT authentication
- Spring Data JPA
- Hibernate ORM
- MySQL 8.0
- Flyway for database migrations
- Lombok for boilerplate reduction
- MapStruct for object mapping

### Tools and Infrastructure
- Maven for build management
- Docker for containerization
- JUnit and Mockito for testing
- Swagger/OpenAPI for API documentation

## System Architecture

The application follows a layered architecture pattern:

1. **Controller Layer** - Handles HTTP requests and responses
2. **Service Layer** - Contains business logic
3. **Repository Layer** - Manages data access
4. **Model Layer** - Defines domain entities
5. **Configuration Layer** - Configures application components
6. **Security Layer** - Manages authentication and authorization

### Domain Model

The core domain entities include:

- **User** - Represents system users with various roles
- **DigitalAsset** - The central entity representing uploaded files
- **Category** - Hierarchical organization of assets
- **Tag** - Keywords for asset categorization
- **Metadata** - Additional asset information
- **Comment** - User interactions on assets
- **Report** - Content flagging system
- **ActivityLog** - User activity tracking

## API Documentation

The REST API is structured around the following main resources:

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `POST /api/auth/refresh-token` - Refresh authentication token
- `POST /api/auth/logout` - User logout
- `POST /api/auth/2fa/enable` - Enable two-factor authentication
- `POST /api/auth/2fa/verify` - Verify two-factor authentication

### Users
- `GET /api/users` - List users (admin only)
- `GET /api/users/{id}` - Get user details
- `PUT /api/users/{id}` - Update user profile
- `DELETE /api/users/{id}` - Delete user account
- `GET /api/users/{id}/assets` - Get user's assets
- `GET /api/users/{id}/activities` - Get user's activity log

### Assets
- `GET /api/assets` - List assets (with filtering options)
- `POST /api/assets` - Upload new asset
- `GET /api/assets/{id}` - Get asset details
- `PUT /api/assets/{id}` - Update asset information
- `DELETE /api/assets/{id}` - Delete asset
- `GET /api/assets/{id}/download` - Download asset
- `GET /api/assets/{id}/comments` - Get asset comments
- `POST /api/assets/{id}/comments` - Add comment to asset
- `POST /api/assets/{id}/report` - Report asset

### Categories
- `GET /api/categories` - List all categories
- `POST /api/categories` - Create new category (admin/manager)
- `GET /api/categories/{id}` - Get category details
- `PUT /api/categories/{id}` - Update category (admin/manager)
- `DELETE /api/categories/{id}` - Delete category (admin/manager)
- `GET /api/categories/{id}/assets` - Get assets in category

### Admin Operations
- `GET /api/admin/reports` - List reported content
- `PUT /api/admin/reports/{id}` - Resolve report
- `GET /api/admin/statistics` - Get system statistics
- `POST /api/admin/verify/{assetId}` - Verify asset content
- `PUT /api/admin/users/{id}/role` - Change user role

## Installation

### Prerequisites
- Java 17 or higher
- Maven 3.6 or higher
- MySQL 8.0
- Docker and Docker Compose (optional)

### Configuration

1. Clone the repository:
   ```
   git clone https://github.com/yourusername/pleaseletmepass.git
   cd pleaseletmepass
   ```

2. Configure database connection in `src/main/resources/application.properties`:
   ```
   spring.datasource.url=jdbc:mysql://localhost:3306/pleaseletmepass
   spring.datasource.username=your_username
   spring.datasource.password=your_password
   ```

3. Set up file storage location:
   ```
   app.file.upload-dir=./uploads
   ```

4. Configure JWT security:
   ```
   app.jwt.secret=your_jwt_secret_key
   app.jwt.expiration=86400000
   ```

## Running the Application

### Using Maven

```
./mvnw spring-boot:run
```

### Using Docker

```
docker-compose up -d
```

The application will be available at `http://localhost:8080`

## Development

### Building the Project

```
./mvnw clean install
```

### Running Tests

```
./mvnw test
```

### Database Migrations

The application uses Flyway for database migrations. New migrations should be added to the `src/main/resources/db/migration` directory following the naming convention `V{version}__{description}.sql`.

### API Documentation

Swagger UI is available at `http://localhost:8080/swagger-ui.html` when running the application locally.

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.
