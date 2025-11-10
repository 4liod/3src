# Cloud3src - Drupal LMS Distribution

![Version](https://img.shields.io/badge/version-1.0.1-blue.svg)
![Drupal](https://img.shields.io/badge/drupal-9%20%7C%2010-blue.svg)
![License](https://img.shields.io/badge/license-GPL--2.0-blue.svg)

Cloud3src is an enterprise-ready Learning Management System (LMS) distribution built on Drupal and powered by Opigno. It provides a complete, pre-configured platform for creating, managing, and delivering online learning experiences.

## 📚 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Quick Start](#quick-start)
- [Documentation](#documentation)
- [Support](#support)
- [License](#license)

## Overview

Cloud3src is a **Drupal installation profile**, not just a theme. It combines:

- **Opigno LMS** - Powerful learning management system core
- **Aristotle Theme** - Modern, responsive learning platform interface
- **Pre-configured Content Types** - Ready-to-use learning resources
- **French Language Support** - Full translations included
- **H5P Integration** - Interactive content capabilities
- **xAPI/Tincan Support** - Learning Record Store (LRS) integration

**Developed by:** 4LIOD
**Drupal Compatibility:** Drupal 9 & 10
**Current Version:** 1.0.1

## Features

### 🎓 Learning Management

- **Learning Paths** - Structured course sequences
- **Course Management** - Create and organize training modules
- **Assessments & Quizzes** - Comprehensive testing capabilities
- **Certificates** - Automatic certificate generation
- **Grading & Reports** - Track learner progress and performance

### 👥 User Management

- **Group System** - Organize learners into cohorts
- **User Profiles** - Customizable learner profiles
- **Private Messaging** - Internal communication system
- **Social Features** - User connections and networking
- **Role-based Access** - Flexible permission system

### 📊 Advanced Features

- **Calendar Integration** - Schedule and track learning activities
- **Dashboard Widgets** - Personalized learning dashboard
- **H5P Content** - Interactive multimedia content
- **File Management** - Public and private file handling
- **Search Functionality** - Full-text content search
- **Mobile App Support** - Compatible with Opigno mobile app
- **xAPI/Tincan** - Learning analytics and LRS integration

### 🎨 Aristotle Theme

- **Responsive Design** - Mobile-friendly interface
- **Customizable Branding** - Logo, colors, and styling
- **Slideshow Support** - Homepage promotional content
- **Menu Customization** - Flexible navigation options
- **Login Page Branding** - Custom login experience

## Requirements

### System Requirements

- **Drupal Core:** ^9 || ^10
- **PHP:** 7.4+ (PHP 8.0+ recommended)
- **Database:** MySQL 5.7.8+ / MariaDB 10.3.7+ / PostgreSQL 12+
- **Web Server:** Apache 2.4+ / Nginx 1.18+
- **Memory:** 256MB minimum (512MB recommended)

### Required Extensions

- **Composer** - Dependency management
- **Private File System** - For secure content delivery
- **GD/ImageMagick** - Image processing
- **PHP Extensions:** json, gd, mbstring, xml, zip

## Quick Start

### Installation

1. **Clone the repository:**
   ```bash
   git clone <repository-url> cloud3src
   cd cloud3src
   ```

2. **Install dependencies:**
   ```bash
   composer install
   ```

3. **Configure your settings.php:**
   - Set up database connection
   - Configure private file system path
   - Set trusted host patterns

4. **Run Drupal installation:**
   ```bash
   drush site:install cloud3src --account-name=admin --account-pass=admin
   ```

   Or use the web installer and select **Cloud3src** as the installation profile.

5. **Configure basic settings:**
   - Upload logo files to `themes/aristotle/assets/`
   - Configure site name and email
   - Set up private file system

For detailed installation instructions, see [INSTALLATION.md](docs/INSTALLATION.md).

## Documentation

Comprehensive documentation is available in the `docs/` directory:

- **[INSTALLATION.md](docs/INSTALLATION.md)** - Detailed installation guide
- **[FEATURES.md](docs/FEATURES.md)** - Complete feature reference
- **[THEME.md](docs/THEME.md)** - Aristotle theme customization
- **[CONFIGURATION.md](docs/CONFIGURATION.md)** - Configuration and settings
- **[USER_GUIDE.md](docs/USER_GUIDE.md)** - End-user documentation
- **[DEVELOPMENT.md](docs/DEVELOPMENT.md)** - Developer guide

## Project Structure

```
cloud3src/
├── config/
│   ├── install/          # Required installation configurations
│   └── optional/         # Optional feature configurations
├── docs/                 # Documentation (you are here)
├── h5plib/              # H5P content libraries
├── images/              # Theme images and assets
├── translations/        # French language files
├── cloud3src.info.yml   # Profile metadata
├── cloud3src.profile    # Profile hooks
├── cloud3src.install    # Installation hooks
├── composer.json        # Dependency definitions
└── README.md           # This file
```

## Main Menu Structure

The distribution includes a pre-configured main menu:

1. **Home** - Dashboard and learning overview
2. **Catalogue** - Browse available courses and training
3. **Calendar** - Schedule and upcoming activities
4. **Statistics** - Progress reports and analytics

## Configuration Files

This distribution includes **134 pre-configured YAML files** including:

- Block placements and layouts
- Content type definitions
- User roles and permissions
- Views and displays
- Image styles
- Text formats and editors
- Opigno LMS settings

All configurations are managed through Drupal's configuration management system.

## Included Translations

- **French (Français)** - Complete Drupal 10.x translations
- Includes translations for:
  - Drupal Core 10.4 & 10.x
  - Group module
  - Twig Field Value module

## Support

### Resources

- **Opigno Documentation:** https://opigno.org/documentation
- **Drupal Documentation:** https://www.drupal.org/docs
- **Aristotle Theme:** https://www.drupal.org/project/aristotle

### Getting Help

For issues and support:

1. Check the documentation in the `docs/` directory
2. Review Drupal and Opigno community forums
3. Contact your system administrator or 4LIOD support

## Contributing

When contributing to this distribution:

1. Follow Drupal coding standards
2. Test all changes in a development environment
3. Update documentation for new features
4. Submit changes through version control

## License

This Drupal distribution is licensed under GPL-2.0. Individual components may have their own licenses:

- Drupal Core: GPL-2.0+
- Opigno Modules: GPL-2.0+
- Aristotle Theme: GPL-2.0+
- Third-party libraries: See composer.json for details

## Credits

**Developed by:** 4LIOD
**Based on:**
- [Drupal](https://drupal.org) - Content Management Framework
- [Opigno LMS](https://opigno.org) - Learning Management System
- [Aristotle Theme](https://www.drupal.org/project/aristotle) - Responsive theme

## Version History

- **1.0.1** - Current release
  - Drupal 9 & 10 compatibility
  - Opigno 3.2.0 integration
  - Aristotle theme 3.2.0
  - French translations included

---

**Note:** This is an installation profile that must be selected during Drupal installation. It cannot be enabled like a regular module on an existing Drupal site.

For more information, see the [complete documentation](docs/).
