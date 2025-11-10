# Installation Guide - Cloud3src

This guide provides detailed instructions for installing the Cloud3src Drupal LMS distribution.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation Methods](#installation-methods)
- [Post-Installation Configuration](#post-installation-configuration)
- [Troubleshooting](#troubleshooting)
- [Next Steps](#next-steps)

## Prerequisites

### System Requirements

Before installing Cloud3src, ensure your server meets these requirements:

#### Server Software

- **Web Server:**
  - Apache 2.4+ with mod_rewrite enabled
  - OR Nginx 1.18+
- **PHP:** 7.4+ (PHP 8.0 or 8.1 recommended)
- **Database:**
  - MySQL 5.7.8+ or MariaDB 10.3.7+
  - OR PostgreSQL 12+
- **Composer:** 2.0+ for dependency management

#### PHP Configuration

Minimum PHP settings in `php.ini`:

```ini
memory_limit = 256M          ; 512M recommended for better performance
max_execution_time = 300     ; Allow time for installation
upload_max_filesize = 64M    ; For course materials upload
post_max_size = 64M
max_input_vars = 3000        ; Required for Drupal forms
```

#### Required PHP Extensions

- `gd` or `imagick` - Image processing
- `json` - JSON handling
- `mbstring` - Multi-byte string support
- `xml` - XML parsing
- `zip` - Archive handling
- `pdo_mysql` or `pdo_pgsql` - Database connectivity
- `opcache` - Recommended for performance

### File System Requirements

**CRITICAL:** Cloud3src requires a **private file system** configured before installation.

1. Create a private files directory **outside** your web root:
   ```bash
   mkdir -p /var/www/private_files
   chmod 775 /var/www/private_files
   chown www-data:www-data /var/www/private_files
   ```

2. This will be configured in `settings.php` (see below)

### Composer

Install Composer globally if not already installed:

```bash
curl -sS https://getcomposer.org/installer | php
mv composer.phar /usr/local/bin/composer
chmod +x /usr/local/bin/composer
```

## Installation Methods

### Method 1: Web-based Installation (Recommended)

#### Step 1: Download and Prepare Files

```bash
# Clone the repository
git clone <repository-url> cloud3src
cd cloud3src

# Install dependencies with Composer
composer install
```

#### Step 2: Create Database

Create a database for your Drupal installation:

**MySQL/MariaDB:**
```sql
CREATE DATABASE cloud3src CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'cloud3src_user'@'localhost' IDENTIFIED BY 'secure_password';
GRANT ALL PRIVILEGES ON cloud3src.* TO 'cloud3src_user'@'localhost';
FLUSH PRIVILEGES;
```

**PostgreSQL:**
```sql
CREATE DATABASE cloud3src;
CREATE USER cloud3src_user WITH PASSWORD 'secure_password';
GRANT ALL PRIVILEGES ON DATABASE cloud3src TO cloud3src_user;
```

#### Step 3: Configure Web Server

**Apache Configuration:**

Create a virtual host configuration:

```apache
<VirtualHost *:80>
    ServerName learning.example.com
    DocumentRoot /var/www/cloud3src/web

    <Directory /var/www/cloud3src/web>
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/cloud3src-error.log
    CustomLog ${APACHE_LOG_DIR}/cloud3src-access.log combined
</VirtualHost>
```

Enable the site and required modules:
```bash
a2ensite cloud3src
a2enmod rewrite
systemctl restart apache2
```

**Nginx Configuration:**

```nginx
server {
    listen 80;
    server_name learning.example.com;
    root /var/www/cloud3src/web;

    index index.php index.html;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ \.php$ {
        fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }

    location ~ /\.ht {
        deny all;
    }
}
```

#### Step 4: Prepare settings.php

Copy the default settings file:

```bash
cd web/sites/default
cp default.settings.php settings.php
chmod 664 settings.php
```

Add the following configuration to `settings.php`:

```php
<?php

// Database configuration
$databases['default']['default'] = [
  'database' => 'cloud3src',
  'username' => 'cloud3src_user',
  'password' => 'secure_password',
  'host' => 'localhost',
  'port' => '3306',
  'driver' => 'mysql',
  'prefix' => '',
  'collation' => 'utf8mb4_unicode_ci',
];

// Private file system (REQUIRED)
$settings['file_private_path'] = '/var/www/private_files';

// Trusted host patterns (update with your domain)
$settings['trusted_host_patterns'] = [
  '^learning\.example\.com$',
  '^www\.learning\.example\.com$',
];

// Hash salt (generate a unique value)
$settings['hash_salt'] = 'your-unique-hash-salt-here';

// Configuration sync directory
$settings['config_sync_directory'] = '../config/sync';
```

Generate a secure hash salt:
```bash
php -r 'echo bin2hex(random_bytes(32)) . "\n";'
```

#### Step 5: Run Web Installer

1. Navigate to your site URL: `http://learning.example.com`
2. Select **Cloud3src** as the installation profile
3. Follow the installation wizard:
   - Choose language (English or French)
   - Verify requirements
   - Configure database (already in settings.php)
   - Configure site information:
     - Site name: Your LMS Name
     - Site email: admin@example.com
     - Admin username: admin
     - Admin password: (secure password)
     - Admin email: admin@example.com
4. Wait for installation to complete (may take 5-10 minutes)

#### Step 6: Secure Permissions

After installation completes:

```bash
cd /var/www/cloud3src/web/sites/default
chmod 444 settings.php
```

### Method 2: Drush Installation (Command Line)

For automated installations or development environments:

#### Step 1: Install Prerequisites

```bash
# Install Drush globally
composer global require drush/drush
export PATH="$HOME/.composer/vendor/bin:$PATH"

# Verify Drush installation
drush --version
```

#### Step 2: Prepare Files

```bash
# Clone and install dependencies
git clone <repository-url> cloud3src
cd cloud3src
composer install
```

#### Step 3: Configure settings.php

Follow Step 4 from Method 1 to create and configure `settings.php`.

#### Step 4: Run Drush Installation

```bash
drush site:install cloud3src \
  --db-url='mysql://cloud3src_user:secure_password@localhost/cloud3src' \
  --site-name='My Learning Platform' \
  --site-mail='admin@example.com' \
  --account-name='admin' \
  --account-pass='secure_admin_password' \
  --account-mail='admin@example.com' \
  -y
```

#### Step 5: Verify Installation

```bash
drush status
drush user:login
```

This will generate a one-time login link for the admin account.

## Post-Installation Configuration

### 1. Private File System Verification

Verify the private file system is working:

1. Navigate to: **Administration → Reports → Status report**
2. Check for "Private file system" - should show green checkmark
3. If red, verify permissions and path in `settings.php`

### 2. Configure Cron

Set up automated cron for background tasks:

**Using system cron:**
```bash
# Add to crontab
crontab -e

# Run cron every hour
0 * * * * cd /var/www/cloud3src && drush cron
```

**Or enable Drupal automated cron:**
- Navigate to: **Administration → Configuration → System → Cron**
- Set interval to 3 hours (or as needed)

### 3. Upload Theme Assets

Copy your branding assets to the Aristotle theme:

```bash
# Logo files
cp your-logo.svg web/themes/contrib/aristotle/assets/4LIOD.svg
cp your-logo-white.svg web/themes/contrib/aristotle/assets/4LIOD-white.svg
cp login-background.jpg web/themes/contrib/aristotle/assets/4LIOD-login-image.jpg
```

Or use the pre-included image:
```bash
cp images/3src_Image_connexion_1600-829_2.jpg web/themes/contrib/aristotle/assets/4LIOD-login-image.jpg
```

### 4. Configure Site Settings

Navigate through these administrative sections:

1. **Basic Site Settings**
   - **Administration → Configuration → System → Basic site settings**
   - Set site name, slogan, email addresses
   - Configure front page path

2. **Regional Settings**
   - **Administration → Configuration → Regional and language**
   - Set timezone
   - Configure date formats
   - Add French language if needed

3. **Performance**
   - **Administration → Configuration → Development → Performance**
   - Enable CSS and JS aggregation
   - Configure caching (for production)

4. **File System**
   - **Administration → Configuration → Media → File system**
   - Verify public and private paths
   - Set default download method

### 5. Configure Opigno Dashboard

Customize the learning dashboard:

1. Navigate to: **Administration → Opigno → Settings → Dashboard**
2. Configure available dashboard widgets
3. Set default dashboard layout
4. Enable/disable specific widgets

### 6. Set Up Email

Configure outgoing mail:

1. Install and enable mailsystem and mimemail (already included)
2. Configure SMTP settings if needed:
   - Use a module like SMTP Authentication Support
   - Or configure PHP's sendmail

### 7. Security Hardening

**Recommended security steps:**

1. **Remove unnecessary files:**
   ```bash
   rm web/INSTALL.txt
   rm web/README.txt
   rm web/core/INSTALL.txt
   ```

2. **Configure security headers** in your web server
3. **Enable HTTPS** with Let's Encrypt:
   ```bash
   certbot --apache -d learning.example.com
   ```

4. **Regular updates:**
   ```bash
   composer update drupal/core --with-dependencies
   drush updatedb
   drush cache:rebuild
   ```

## Troubleshooting

### Installation Fails with "Private file system not configured"

**Solution:**
1. Ensure directory exists: `mkdir -p /var/www/private_files`
2. Set correct permissions: `chmod 775 /var/www/private_files`
3. Set correct owner: `chown www-data:www-data /var/www/private_files`
4. Verify path in `settings.php`

### "Class not found" Errors

**Solution:**
```bash
composer install
composer dump-autoload
drush cache:rebuild
```

### Memory Limit Errors

**Solution:**
Increase PHP memory limit in `php.ini` or `.htaccess`:
```
php_value memory_limit 512M
```

### White Screen of Death (WSOD)

**Solution:**
1. Check PHP error logs
2. Enable Drupal error display temporarily in `settings.php`:
   ```php
   $config['system.logging']['error_level'] = 'verbose';
   ```
3. Clear cache: `drush cache:rebuild`

### Permission Denied Errors

**Solution:**
```bash
# Fix file permissions
cd /var/www/cloud3src
find web/sites/default/files -type d -exec chmod 775 {} \;
find web/sites/default/files -type f -exec chmod 664 {} \;
chown -R www-data:www-data web/sites/default/files
```

### Cannot Access Admin Pages

**Solution:**
1. Clear cache: `drush cache:rebuild`
2. Rebuild permissions: `drush php:eval "node_access_rebuild();"`
3. Log in with one-time link: `drush user:login`

## Next Steps

After successful installation:

1. **Configure Theme** - See [THEME.md](THEME.md) for Aristotle theme customization
2. **Explore Features** - See [FEATURES.md](FEATURES.md) for LMS capabilities
3. **Create Content** - Start creating courses and learning paths
4. **Configure Users** - Set up user roles and permissions
5. **Test System** - Create test courses and user accounts

## Additional Resources

- **Drupal Documentation:** https://www.drupal.org/docs/getting-started
- **Opigno Documentation:** https://opigno.org/documentation
- **Composer Documentation:** https://getcomposer.org/doc/
- **Drush Documentation:** https://www.drush.org/

## Support

For installation issues:

1. Check the [Troubleshooting](#troubleshooting) section above
2. Review Drupal's installation documentation
3. Contact your system administrator
4. Consult 4LIOD support resources

---

**Next:** [Configure the Aristotle Theme →](THEME.md)
