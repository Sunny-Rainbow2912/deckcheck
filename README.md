# DeckCheck

A comprehensive vessel management and maintenance tracking system designed to streamline operations, maintenance scheduling, and compliance tracking for maritime vessels.

## 🚢 Overview

DeckCheck is a web-based application built for crew management, vessel maintenance, and operational compliance. It provides a smart way to manage admin and SMS compliance, offering solutions built by crew for crew. The system enables efficient tracking of equipment maintenance, work orders, deficiencies, and vessel operations.

## ✨ Features

### Vessel Management

- **Multi-Vessel Support**: Manage multiple vessels with complete scoping and access control
- **Vessel Profiles**: Comprehensive vessel information including specifications, contact details, and documentation
- **Vessel Switching**: Easy navigation between accessible vessels for authorized users

### Maintenance & Work Orders

- **Maintenance Templates**: Create reusable maintenance templates with categories, intervals, and tasks
- **Template Inheritance**: Automatic creation of equipment intervals and work orders from templates
- **Work Order Management**: Generate, track, and complete work orders with task breakdowns
- **Equipment Tracking**: Comprehensive equipment inventory with maintenance history
- **Interval Management**: Schedule recurring maintenance with custom intervals and facilitators

### Deficiency Management

- **Deficiency Tracking**: Record, update, and resolve vessel deficiencies
- **Status Workflow**: Track deficiency status from identification to resolution
- **History & Updates**: Maintain complete audit trail of deficiency changes

### File Management

- **S3 Integration**: Secure file storage with AWS S3 support
- **File Attachments**: Polymorphic attachment system for any model
- **File Deduplication**: Automatic file deduplication using SHA256 hashing
- **Multiple File Types**: Support for documents, images, manuals, and reports

### User & Access Control

- **Role-Based Access**: Multiple user roles (superadmin, staff, dev, user)
- **Vessel Access Control**: System users can access all vessels; regular users access only vessels they're boarded on
- **Staff Management**: Comprehensive admin panel for managing staff and permissions
- **User Invitations**: Invite users via email with role-based permissions

### Additional Features

- **Inventory Management**: Track vessel inventory and equipment
- **Reports & Analytics**: Generate reports and view business intelligence
- **Theme System**: Customizable themes and user preferences
- **Dashboard**: Overview of vessel operations, pending tasks, and key metrics

## 🛠️ Technology Stack

### Backend

- **Framework**: Laravel 12
- **PHP**: 8.2+
- **Database**: MySQL/PostgreSQL (configurable)
- **Storage**: AWS S3 for file storage
- **Queue**: Laravel Queue System
- **Testing**: Pest PHP

### Frontend

- **CSS Framework**: Tailwind CSS 3
- **JavaScript**: Alpine.js
- **Build Tool**: Vite 6
- **Forms**: Tailwind Forms plugin

### Development Tools

- **Code Style**: Laravel Pint
- **Blade Formatter**: blade-formatter
- **Prettier**: For JS/CSS formatting
- **Git Hooks**: Husky with lint-staged

## 📋 Requirements

- PHP 8.2 or higher
- Composer 2.x
- Node.js 18+ and npm
- MySQL 8.0+ or PostgreSQL 13+
- AWS S3 account (for file storage)
- Redis (optional, for queues and caching)

## 🚀 Installation

1. **Clone the repository**

   ```bash
   git clone git@github.com:Sunny-Rainbow2912/deckcheck.git
   cd deckcheck
   ```

2. **Install PHP dependencies**

   ```bash
   composer install
   ```

3. **Install Node dependencies**

   ```bash
   npm install
   ```

4. **Environment setup**

   ```bash
   cp .env.example .env
   php artisan key:generate
   ```

5. **Configure environment**

   Edit `.env` file with your database credentials, AWS S3 credentials, and other settings:

   ```env
   DB_CONNECTION=mysql
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_DATABASE=deckcheck
   DB_USERNAME=your_username
   DB_PASSWORD=your_password

   AWS_ACCESS_KEY_ID=your_access_key
   AWS_SECRET_ACCESS_KEY=your_secret_key
   AWS_DEFAULT_REGION=us-east-1
   AWS_BUCKET=your_bucket_name
   ```

6. **Run migrations**

   ```bash
   php artisan migrate
   ```

7. **Seed database (optional)**

   ```bash
   php artisan db:seed
   ```

8. **Build assets**

   ```bash
   npm run build
   ```

9. **Set up storage directories**
   ```bash
   php setup-directories.php
   ```

## 🔧 Development

### Running the application

For development with hot reloading:

```bash
composer dev
```

Or run individually:

```bash
# Terminal 1: Laravel server
php artisan serve

# Terminal 2: Vite dev server
npm run dev

# Terminal 3: Queue worker
php artisan queue:listen

# Terminal 4: Logs
php artisan pail
```

### Code Formatting

Format PHP code:

```bash
composer format:php
# or
vendor/bin/pint
```

Format Blade templates:

```bash
npm run format:blade
```

Format JavaScript/CSS:

```bash
npm run format:prettier
```

### Testing

Run tests:

```bash
composer test
# or
php artisan test
```

## 📚 Documentation

Comprehensive documentation is available in the `docs/` directory:

- **[Main Documentation](docs/README.md)** - Overview and documentation index
- **[Vessel Access System](docs/VESSEL_ACCESS_SYSTEM_DOCUMENTATION.md)** - Access control documentation
- **[User Management](docs/USER_MANAGEMENT_README.md)** - User roles and permissions
- **[Staff Management](docs/STAFF_MANAGEMENT_README.md)** - Admin panel and staff management
- **[File Upload System](docs/FILE_UPLOAD_SYSTEM.md)** - File storage and attachment system
- **[Maintenance Templates](docs/MAINTENANCE_TEMPLATES_AND_INHERITANCE.md)** - Maintenance template inheritance
- **[Theme System](docs/THEME_SYSTEM.md)** - Theming and customization

## 🏗️ Project Structure

```
deckcheck/
├── app/
│   ├── Console/Commands/     # Artisan commands
│   ├── Http/
│   │   ├── Controllers/     # Application controllers
│   │   ├── Middleware/      # Custom middleware
│   │   └── Requests/        # Form request validation
│   ├── Mail/                # Email notifications
│   ├── Models/              # Eloquent models
│   ├── Observers/           # Model observers
│   ├── Providers/           # Service providers
│   ├── Services/            # Business logic services
│   └── View/Components/     # Blade components
├── database/
│   ├── migrations/          # Database migrations
│   ├── seeders/             # Database seeders
│   └── factories/           # Model factories
├── docs/                    # Documentation
├── public/                  # Public assets
├── resources/
│   ├── css/                 # Stylesheets
│   ├── js/                  # JavaScript files
│   └── views/               # Blade templates
├── routes/                  # Route definitions
└── tests/                   # Test files
```

## 🔐 Security

- **Vessel Access Control**: All routes protected by vessel access middleware
- **Role-Based Permissions**: Multiple security layers with role checking
- **CSRF Protection**: Laravel's built-in CSRF protection
- **File Security**: Secure file storage with proper access controls
- **Password Hashing**: Bcrypt password hashing
- **SQL Injection Prevention**: Eloquent ORM with parameter binding

## 👥 User Roles

- **superadmin**: Full system access, can manage all vessels and users
- **staff**: Vessel management, maintenance tools, reports
- **dev**: Development access
- **user**: Regular user with vessel-specific access based on boarding records

## 🐳 Docker Support

Docker configuration files are included:

- `docker-compose.yml` - Main Docker Compose configuration
- `docker-compose.override.yml` - Local overrides
- `Dockerfile` - Application container definition

## 📝 License

This project is proprietary software. All rights reserved.

## 🤝 Contributing

This is a private repository. For questions or support, please contact the development team.

## 📧 Contact

For inquiries or support, please contact: rainbow18831@gmail.com

---

**Built with ❤️ for maritime professionals**
