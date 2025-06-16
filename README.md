# Airbnb Clone Project 
## Project Description
This project is a full-stack clone of the popular accommodation booking platform Airbnb. The goal is to build a fully functional web application where users can:

- Browse property listings
- View detailed property information
- Perform property searches with filters
- Complete bookings through a secure checkout
- Manage user authentication

 ---
## Tech Stack
### Frontend:
- HTML
- CSS
- JavaScript
- React (or similar framework)
## Technology Stack

### Django
A high-level Python web framework used for building the RESTful API. It handles URL routing, request handling, user authentication, ORM (Object Relational Mapping), and many backend business logics efficiently.

### Django REST Framework (DRF)
An extension of Django that provides powerful tools and features to easily create and manage RESTful APIs. It simplifies serialization, authentication, and API versioning.

### PostgreSQL
A powerful open-source relational database system used for data storage. It efficiently manages structured data such as user information, property listings, bookings, payments, and more.

### GraphQL
A query language for APIs that allows clients to request exactly the data they need. It helps optimize data fetching and reduces over-fetching or under-fetching issues common in REST APIs.

### Celery
An asynchronous task queue used to handle background tasks such as sending notifications, processing payments, and managing booking confirmations without blocking the main application flow.

### Redis
An in-memory data store used for caching frequently accessed data to improve application performance. It also serves as a broker for Celery tasks and manages session data.

### Docker
A containerization platform that packages the entire application with its dependencies into portable containers, ensuring consistent development, testing, and deployment environments.

### CI/CD Pipelines
Automated Continuous Integration and Continuous Deployment pipelines that automatically run tests, check code quality, and deploy updates to production environments, ensuring fast, safe, and reliable releases.
---


### Version Control:
- Git & GitHub

### Design Tools:
- Figma (for UI/UX design)

## Learning Objectives
- Learn to implement responsive UI/UX designs
- Understand how to structure a complex web application
- Practice working in a team with defined roles
- Develop skills in component-based frontend architecture
- Learn best practices for web application development

## Project Repository
GitHub Repository: [airbnb-clone-project](https://github.com/mercyXp/airbnb-clone-project)


## UI/UX Design Planning

### Design Goals

- Create intuitive booking flow.
- Maintain visual consistency.
- Ensure fast loading times.
- Prioritize mobile responsiveness.

### Key Features

- Property search and filtering.
- Detailed property viewing.
- Secure checkout process.
- User authentication.

### Primary Pages

| Page                 | Description |
|-----------------------|-------------|
| **Property Listing View** | Grid display of available properties with filters. |
| **Listing Detailed View** | Complete property details with images and booking form. |
| **Simple Checkout View**  | Streamlined payment and booking confirmation. |

### Importance of User-Friendly Design

A well-designed booking system reduces friction in the user journey, increases conversion rates, and improves customer satisfaction. Clear navigation, intuitive interfaces, and responsive design are critical for success.

---

## Figma Design Specifications

### Color Styles

- **Primary:** `#FF5A5F`
- **Secondary:** `#008489`
- **Background:** `#FFFFFF`
- **Text:** `#222222`
- **Secondary Text:** `#717171`

### Typography

- **Primary Font:** Circular, Medium (500), 16px
- **Headings:** Circular, Bold (700), 24px–32px
- **Secondary Text:** Circular, Book (400), 14px

---

## Team Roles 

| Role | Responsibilities |
|------|-------------------|
| **Project Manager** | Oversees timeline, coordinates team, manages deliverables. |
| **Frontend Developers** | Implements UI components, ensures responsive design. |
| **Backend Developers** | Builds APIs, manages database, implements business logic. |
| **Designers** | Creates mockups, maintains design system, ensures UX quality. |
| **QA/Testers** | Writes test cases, performs testing, reports bugs. |
| **DevOps Engineers** | Manages deployment, CI/CD pipeline, server infrastructure. |
| **Product Owner** | Defines requirements, prioritizes features, represents stakeholders. |
| **Scrum Master** | Facilitates agile processes, removes blockers, organizes meetings. |

---

## UI Component Patterns

### Planned Components

#### Navbar

- Logo
- Search bar
- User navigation
- Responsive menu

#### Property Card

- Property image
- Basic details (price, location, rating)
- Favorite button
- Responsive layout

#### Footer

- Site links
- Company information
- Social media links
- Copyright information

> Each component will be designed for reusability and consistency across the application.
>
## Database Design

### Key Entities and Relationships

---

### 1️⃣ Users

Represents users of the platform (guests and hosts).

**Fields:**
- `id` (Primary Key)
- `username`
- `email`
- `password` (hashed)
- `first_name`
- `last_name`
- `profile_picture`
- `is_host` (Boolean to distinguish hosts from regular users)

**Relationships:**
- A user can own multiple properties (if `is_host` is true).
- A user can make multiple bookings.
- A user can leave multiple reviews.

---

### 2️⃣ Properties

Represents the listings available for booking.

**Fields:**
- `id` (Primary Key)
- `host_id` (Foreign Key → Users)
- `title`
- `description`
- `address`
- `price_per_night`
- `max_guests`
- `amenities`
- `created_at`

**Relationships:**
- A property belongs to one host (user).
- A property can have multiple bookings.
- A property can have multiple reviews.

---

### 3️⃣ Bookings

Represents reservations made by users.

**Fields:**
- `id` (Primary Key)
- `user_id` (Foreign Key → Users)
- `property_id` (Foreign Key → Properties)
- `check_in_date`
- `check_out_date`
- `total_price`
- `status` (Pending, Confirmed, Cancelled)

**Relationships:**
- A booking belongs to one user and one property.
- A booking can have one related payment.

---

### 4️⃣ Reviews

Represents feedback left by users on properties.

**Fields:**
- `id` (Primary Key)
- `user_id` (Foreign Key → Users)
- `property_id` (Foreign Key → Properties)
- `rating` (e.g., 1–5 stars)
- `comment`
- `created_at`

**Relationships:**
- A review belongs to one user and one property.

---

### 5️⃣ Payments

Represents payment transactions for bookings.

**Fields:**
- `id` (Primary Key)
- `booking_id` (Foreign Key → Bookings)
- `payment_date`
- `amount`
- `payment_method`
- `payment_status` (Pending, Completed, Failed)

**Relationships:**
- A payment belongs to one booking.

---

### Summary of Relationships

- **Users** can have multiple **Properties**, **Bookings**, and **Reviews**.
- **Properties** belong to a **User** (host), and can have multiple **Bookings** and **Reviews**.
- **Bookings** belong to both **Users** and **Properties**.
- **Payments** are linked to a **Booking**.
- **Reviews** belong to both **Users** and **Properties**.

---
## Feature Breakdown

### 1️⃣ User Management

The system allows users to register, log in, and manage their profiles. Users can be either guests or hosts. Hosts can list properties, while guests can book properties and leave reviews. Secure authentication and role-based access control ensure a safe and personalized experience.

---

### 2️⃣ Property Management

Hosts can create, update, and delete property listings. Each property includes details such as location, price, images, amenities, and availability. This feature allows the platform to maintain an up-to-date catalog of accommodations for potential guests.

---

### 3️⃣ Booking System

Guests can search for available properties, select dates, and make bookings. The system checks property availability, calculates total costs, and handles reservation status (pending, confirmed, canceled). This is the core functionality that enables users to reserve stays.

---

### 4️⃣ Payment Integration

A secure payment system processes transactions for bookings. It handles payment methods, calculates amounts based on booking details, and manages payment status. This ensures a smooth and reliable financial process for both guests and hosts.

---

### 5️⃣ Reviews and Ratings

Guests can leave reviews and ratings after completing their stays. Reviews include written feedback and star ratings, helping future guests make informed decisions and providing valuable feedback to hosts.

---

### 6️⃣ Search and Filtering

Guests can search for properties based on location, price, amenities, availability, and other filters. This feature enhances user experience by allowing quick access to relevant listings that match guest preferences.

---

### 7️⃣ Notifications

The system sends notifications for important events such as booking confirmations, cancellations, and payment updates. Notifications keep both guests and hosts informed throughout the booking process.

---

### 8️⃣ Admin Dashboard (Optional Advanced Feature)

An administrative panel allows platform administrators to oversee user activity, manage listings, handle disputes, and monitor overall platform health. This feature supports platform governance and maintenance.

## API Security

Securing the backend APIs is essential to protect user data, ensure the integrity of transactions, and maintain trust on the platform. Below are the key security measures that will be implemented:

---

### 1️⃣ Authentication

**Description:**  
We will implement secure authentication using JSON Web Tokens (JWT) or OAuth2 to verify the identity of users before granting access to protected endpoints.

**Why it's important:**  
- Prevents unauthorized access to user accounts.
- Ensures that only authenticated users can make bookings, post reviews, or modify properties.

---

### 2️⃣ Authorization

**Description:**  
Role-based access control (RBAC) will be used to restrict users to only the actions they are permitted to perform. For example, only property owners can edit their own listings.

**Why it's important:**  
- Prevents privilege escalation.
- Protects sensitive operations and enforces correct user permissions.

---

### 3️⃣ Data Validation and Sanitization

**Description:**  
All incoming data will be validated and sanitized to prevent injection attacks (SQL injection, XSS).

**Why it's important:**  
- Protects the database and frontend from malicious data.
- Ensures system stability and data integrity.

---

### 4️⃣ Rate Limiting & Throttling

**Description:**  
Implement rate limiting to control the number of requests a user can make in a certain period, preventing abuse and DoS attacks.

**Why it's important:**  
- Protects the server from being overloaded.
- Prevents brute-force attacks on login endpoints.

---

### 5️⃣ Secure Data Transmission

**Description:**  
Enforce HTTPS across all endpoints to encrypt data in transit between client and server.

**Why it's important:**  
- Prevents eavesdropping and man-in-the-middle attacks.
- Secures sensitive information such as login credentials and payment data.

---

### 6️⃣ Payment Security

**Description:**  
Integrate with secure, PCI-compliant payment gateways (e.g., Stripe, PayPal). Sensitive financial data will never be stored on our servers.

**Why it's important:**  
- Ensures compliance with financial regulations.
- Protects both guests and hosts from fraud.

---

### 7️⃣ Logging and Monitoring

**Description:**  
Maintain logs for critical API events and monitor for suspicious activity.

**Why it's important:**  
- Enables quick detection and response to security breaches.
- Helps in auditing and forensic analysis after incidents.

---

### 8️⃣ Environment Configuration Security

**Description:**  
Sensitive credentials such as API keys, database passwords, and secret keys will be stored in environment variables and secured through proper secret management.

**Why it's important:**  
- Prevents accidental exposure of sensitive information in code repositories.
- Ensures secure deployment practices.

## CI/CD Pipeline

### What is CI/CD?

CI/CD stands for Continuous Integration and Continuous Deployment (or Delivery). It is a set of automated processes that allow code changes to be automatically tested, integrated, and deployed to production in a reliable and efficient way.

- **Continuous Integration (CI):** Automatically integrates code changes from multiple developers into a shared repository several times a day. It runs automated tests to ensure that new code does not break existing functionality.
- **Continuous Deployment (CD):** Automatically deploys tested and approved code changes to production or staging environments without manual intervention.

---

### Why CI/CD is Important for This Project

- 🚀 **Faster Development:** Speeds up the release cycle by automating testing and deployment.
- ✅ **Improved Code Quality:** Early detection of bugs and integration issues.
- 🔒 **More Reliable Deployments:** Reduces human error by automating the deployment process.
- 👥 **Better Collaboration:** Allows multiple team members to work together efficiently without conflicts.
- 🛡️ **Ensures Stability:** Automated tests ensure that the application remains stable even as new features are added.

---

### Tools Used

- **GitHub Actions:** For automating the CI/CD workflows, running tests, building Docker images, and deploying to servers.
- **Docker:** For containerizing the application, ensuring consistent environments across development, testing, and production.
- **Docker Compose:** For managing multi-container Docker applications.
- **AWS / DigitalOcean / Render / Heroku:** (Optional) For hosting and deploying the application.
- **PostgreSQL:** Production-ready database integration within the CI/CD pipeline.
- **Coverage Tools (e.g. Codecov):** For monitoring test coverage and code quality.

---

### CI/CD Workflow Overview

1. Developer pushes code to GitHub repository.
2. GitHub Actions triggers automated tests and code checks.
3. Docker builds and tests containers.
4. If tests pass, Docker image is deployed to staging or production server.
5. Monitoring tools ensure application health post-deployment.

