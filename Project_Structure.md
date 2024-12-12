**World Hotels (WH) Booking System**
### **1. Project Directory Structure**

```
WH-Booking-System/
├── client/                      # Front-End
│   ├── public/                  # Static assets
│   │   ├── images/              # Images
│   │   ├── css/                 # CSS files
│   │   ├── js/                  # JavaScript files
│   │   └── index.html           # Main HTML file
│   ├── templates/               # HTML templates (Flask Jinja2)
│   │   ├── layout.html          # Base template
│   │   ├── home.html            # Home Page template
│   │   ├── booking.html         # Booking Page template
│   │   ├── admin_dashboard.html # Admin Dashboard template
│   │   ├── login.html           # Login Page template
│   │   └── register.html        # Registration Page template
│   └── static/                  # Flask static files
│       ├── css/                 # CSS files
│       ├── js/                  # JavaScript files
│       └── images/              # Images
│
├── app/                         # Flask Application
│   ├── __init__.py              # Initialize Flask app
│   ├── config.py                # Configuration settings
│   ├── models.py                # Database models
│   ├── routes/                  # Routes for Flask views
│   │   ├── user_routes.py       # Routes for user-related operations
│   │   ├── admin_routes.py      # Routes for admin-related operations
│   │   └── booking_routes.py    # Routes for booking operations
│   ├── services/                # Business logic (e.g., discounts, cancellations)
│   ├── utils/                   # Utility functions (validation, formatting)
│   ├── forms.py                 # Flask-WTF forms
│   └── templates/               # Jinja2 templates (see above)
│
├── database/                    # Database scripts
│   ├── migrations/              # Alembic migration files
│   ├── seeders/                 # Initial seed data for testing
│   └── schema.sql               # SQL schema (if using SQL-based DB)
│
├── tests/                       # Testing suite
│   ├── unit/                    # Unit tests
│   ├── integration/             # Integration tests
│   ├── e2e/                     # End-to-end tests
│   └── test-config.py           # Test configuration
│
├── docs/                        # Documentation
│   ├── ERD.png                  # Entity Relationship Diagram
│   ├── API-Documentation.md     # REST API Documentation
│   ├── SystemDesign.pdf         # System architecture and design explanation
│   └── Sitemap.pdf              # Sitemap of the system
│
├── scripts/                     # Scripts for deployment and automation
│   ├── build.sh                 # Build script
│   ├── deploy.sh                # Deployment script
│   └── setup.sh                 # Initial setup script
│
├── .env                         # Environment variables
├── .gitignore                   # Files and directories to ignore in Git
├── README.md                    # Project overview
└── docker-compose.yml           # Docker Compose file for containers
```

---

### **2. Key Features in Each Section**

#### **Front-End**
- **Flask Templates (Jinja2)**:
  - Use Jinja2 for dynamic rendering of HTML pages.
  - Templates for pages like Home, Booking, Admin Dashboard.
- Responsive Design:
  - Use **Bootstrap** or **TailwindCSS** for styling.
- Components:
  - Header: Navigation bar with login/logout.
  - Footer: Quick links and social media.
  - Booking Form: Inputs for dates, destination, room type, guests.
  - Admin Dashboard: Hotel management and report generation UI.
  - User Dashboard: Booking history and profile management.

#### **Back-End (Flask)**
- Features:
  - RESTful API design using **Flask-RESTful** (optional for advanced setups).
  - Authentication:
    - **Flask-Login** for user sessions.
    - Password encryption using **bcrypt**.
  - Role-based Access Control (User/Admin).
  - Business Logic:
    - Discount calculations.
    - Cancellation fee management.
    - Currency conversion using APIs like **exchangeratesapi.io**.
- **Structure**:
  - `__init__.py`: Flask app factory pattern.
  - `models.py`: SQLAlchemy models for database entities.
  - `routes/`: Separate files for modular route handling.
  - `services/`: Implement business logic and third-party integrations.
  - `utils/`: Common helper functions like input validations.

#### **Database**
- Type: **MySQL**, **PostgreSQL**, or **SQLite** (for development).
- ORM: Use **SQLAlchemy** with Flask-Migrate for migrations.
- ERD:
  - **Users Table**: User details (name, email, hashed password, role).
  - **Hotels Table**: Hotel details (name, city, capacity, rates, seasons).
  - **Rooms Table**: Room details (type, price, capacity, status).
  - **Bookings Table**: Booking details (user_id, room_id, dates, discount, status).
  - **Admin Logs Table**: Admin actions for auditing.
- Relationships:
  - One-to-many: Hotel → Rooms.
  - One-to-many: User → Bookings.

#### **Deployment**
- **Containerization**: Use Docker for Flask and database.
  - Flask app container serves the API and templates.
  - Database container for MySQL/PostgreSQL.
- **CI/CD Pipeline**: GitHub Actions or Jenkins for automated testing and deployment.
- Hosting:
  - Use **AWS Elastic Beanstalk**, **Google Cloud Run**, or **Heroku** for Flask app hosting.
  - Use managed databases like **AWS RDS** for scalability.

---

### **3. Workflow**

1. **Frontend**
   - Design HTML templates with dynamic placeholders using Jinja2.
   - Add Bootstrap/TailwindCSS for responsiveness.

2. **Backend**
   - Initialize Flask app and set up the factory pattern.
   - Install dependencies: `Flask`, `Flask-SQLAlchemy`, `Flask-Migrate`, `Flask-WTF`, `Flask-Login`.
   - Create routes for `/users`, `/bookings`, `/hotels`.

3. **Database**
   - Design database schema and implement migrations with Flask-Migrate.
   - Seed initial data for development testing.

4. **Testing**
   - Write unit tests using **pytest**.
   - Use tools like **Postman** or **Swagger UI** for API testing.

5. **Documentation**
   - Create an API documentation file (Markdown or Swagger UI).
   - Maintain system design diagrams and decisions.

6. **Deployment**
   - Build Docker containers.
   - Use Docker Compose to manage Flask app and database containers.
   - Deploy to a cloud provider with HTTPS enabled.

---

### **4. Non-Functional Requirements**
- **Security**:
  - Implement HTTPS.
  - Use Flask-Session for secure session handling.
- **Performance**:
  - Use caching (e.g., Flask-Caching or Redis) for repeated queries.
  - Optimize database queries using indexes.
- **Scalability**:
  - Design stateless Flask app for horizontal scaling.
  - Use a load balancer for traffic distribution.

---
