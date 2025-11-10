# Configuration Guide - Cloud3src

This guide covers common configuration tasks and customization options for the Cloud3src LMS distribution.

## Table of Contents

- [Initial Configuration](#initial-configuration)
- [Site Settings](#site-settings)
- [User Configuration](#user-configuration)
- [Content Configuration](#content-configuration)
- [Learning Path Configuration](#learning-path-configuration)
- [Performance Configuration](#performance-configuration)
- [Security Configuration](#security-configuration)
- [Integration Configuration](#integration-configuration)

## Initial Configuration

### First Steps After Installation

Complete these tasks immediately after installing Cloud3src:

#### 1. Site Information

Navigate to: **Configuration → System → Basic site settings**

Configure:
- **Site name:** Your organization or platform name
- **Slogan:** Optional tagline
- **Email address:** System email (no-reply@example.com)
- **Front page:** Path to homepage (default: `/dashboard`)
- **403 page:** Access denied page (default: `/user/login`)
- **404 page:** Page not found (default: `/node`)

**Example Configuration:**
```
Site name: Acme Learning Platform
Slogan: Excellence in Online Education
Email address: support@acmelearning.com
Front page: /dashboard
```

#### 2. Regional Settings

Navigate to: **Configuration → Regional and language → Regional settings**

Configure:
- **Default country:** Your primary location
- **First day of week:** Monday or Sunday
- **Default time zone:** Server timezone
- **User timezone selection:** Allow users to set their timezone

**Date Formats:**

Navigate to: **Configuration → Regional and language → Date and time formats**

Recommended formats:
- **Default long:** `l, F j, Y - H:i` (Monday, January 15, 2025 - 14:30)
- **Default medium:** `D, m/d/Y - H:i` (Mon, 01/15/2025 - 14:30)
- **Default short:** `m/d/Y - H:i` (01/15/2025 - 14:30)

#### 3. Add French Language (If Needed)

Navigate to: **Configuration → Regional and language → Languages**

The distribution includes French translations in `/translations/fr/`:
- Drupal 10.4 French
- Drupal 10.x French
- Group module French
- Twig Field Value French

**To activate French:**

1. Click "Add language"
2. Select "French" (Français)
3. Click "Add language"
4. Navigate to **Configuration → Regional and language → Translate interface → Import**
5. Import .po files from `/translations/fr/`
6. Set default language or allow users to choose

#### 4. File System Configuration

Navigate to: **Configuration → Media → File system**

Verify configuration:
- **Public file system path:** `sites/default/files` (auto-configured)
- **Private file system path:** `/var/www/private_files` (configured in settings.php)
- **Default download method:** Public or Private (choose based on needs)

**Temporary directory:** Usually `/tmp` - verify it exists and is writable.

**Important:** Private file system is REQUIRED for secure course materials.

## Site Settings

### Homepage Configuration

#### Option 1: Dashboard as Homepage (Default)

Navigate to: **Configuration → System → Basic site settings**

Set front page to: `/dashboard`

This shows the personalized Opigno dashboard to logged-in users.

#### Option 2: Custom Homepage

**Create a custom homepage:**

1. Navigate to: **Content → Add content → Page**
2. Create homepage content:
   - Title: "Welcome"
   - Body: Homepage content
   - Don't display title (if using theme slideshow)
3. Save and note the URL (e.g., `/node/1`)
4. Navigate to: **Configuration → System → Basic site settings**
5. Set front page to: `/node/1`

**Using Aristotle Homepage Slideshow:**

See [THEME.md](THEME.md) for slideshow configuration.

### Menu Configuration

#### Main Navigation Menu

Navigate to: **Structure → Menus → Main navigation**

**Default Menu Structure:**
```
Home (/)
├── Catalogue (/training_catalogue)
├── Calendar (/calendar)
└── Statistics (/statistics)
```

**Adding Custom Menu Items:**

1. Click "Add link"
2. Configure:
   - **Menu link title:** Display text
   - **Link:** URL path or external URL
   - **Description:** Optional tooltip
   - **Enabled:** Check to show
   - **Show as expanded:** Show child items
   - **Parent:** Select parent item
   - **Weight:** Order in menu (lower numbers first)
3. Save

**Example Custom Menu:**
```
Home (/)
├── Catalogue (/training_catalogue)
├── My Courses (/user/[uid]/courses)
├── Calendar (/calendar)
├── Forum (/forum)
├── Statistics (/statistics)
└── Help (/help)
```

#### User Account Menu

Navigate to: **Structure → Menus → Account menu**

Pre-configured links:
- My account
- Log out

**Adding Profile Link:**
```
Menu link title: My Profile
Link: /user
Enabled: ✓
Weight: -10
```

### Block Configuration

Navigate to: **Structure → Block layout**

**Key Block Regions (Aristotle theme):**

1. **Header:**
   - Site branding (logo)
   - Main navigation
   - Search block (optional)

2. **Content:**
   - Main page content
   - System messages
   - Help text

3. **Sidebar First:**
   - User account block
   - Navigation blocks
   - Calendar upcoming events

4. **Footer:**
   - Footer menu
   - Social links
   - Copyright text

**Adding Custom Blocks:**

1. Navigate to: **Structure → Block layout → Custom block library**
2. Click "Add custom block"
3. Choose block type (Basic block)
4. Configure:
   - Block description (admin label)
   - Body (content)
5. Save
6. Navigate back to **Block layout**
7. Click "Place block" in desired region
8. Configure visibility settings
9. Save

## User Configuration

### User Registration

Navigate to: **Configuration → People → Account settings → Registration and cancellation**

**Registration Options:**

1. **Administrators only:**
   - No self-registration
   - Admin creates all accounts
   - Best for controlled environments

2. **Visitors:**
   - Self-registration allowed
   - No approval needed
   - Best for open platforms

3. **Visitors, but administrator approval is required:**
   - Self-registration with approval
   - Moderator reviews applications
   - Best for semi-public platforms

**Recommended for LMS:** Administrators only or approval required

**Email Notifications:**

Configure automated emails:
- **Welcome (new user created by admin):** Enabled
- **Welcome (awaiting approval):** Enabled
- **Welcome (no approval required):** Enabled
- **Password recovery:** Enabled
- **Account activation:** Enabled
- **Account blocked:** Enabled
- **Account cancellation confirmation:** Enabled

### Password Policies

Navigate to: **Configuration → People → Account settings → Account settings**

Configure:
- **Password strength:** Display password strength indicator
- Require secure passwords (via Password Policy module - install separately)

**Recommended Password Requirements:**
- Minimum 8 characters
- Mix of uppercase and lowercase
- At least one number
- At least one special character

### User Fields

Navigate to: **Configuration → People → Account settings → Manage fields**

**Default User Picture Field:**
Already configured. Customize:
- Allowed file extensions
- Maximum upload size
- Image resolution

**Adding Custom Fields:**

1. Click "Add field"
2. Choose field type:
   - Text (plain or formatted)
   - List (select options)
   - Boolean (checkbox)
   - Date
   - Entity reference
3. Configure field settings
4. Set required/optional
5. Save

**Useful Custom Fields:**
- Job title
- Department
- Phone number
- Biography
- LinkedIn profile
- Skills/interests

### User Roles & Permissions

Navigate to: **Administration → People → Roles**

**Default Roles:**
- Anonymous user
- Authenticated user
- Administrator
- Student manager
- Content manager
- User manager

**Creating Custom Roles:**

1. Click "Add role"
2. Enter role name (e.g., "Instructor")
3. Save
4. Configure permissions:
   - Navigate to: **People → Permissions**
   - Check appropriate permissions for new role
   - Save permissions

**Common Permission Sets:**

**Instructor Role:**
- Create and edit modules
- Grade student work
- View student progress
- Access reports
- Moderate forum discussions

**Department Manager Role:**
- Enroll users in training
- View department statistics
- Create groups
- Assign roles within groups

## Content Configuration

### Content Types

Navigate to: **Structure → Content types**

**Pre-configured Content Types:**
- **Page:** Static information pages
- **Module:** Learning modules
- **Quiz:** Assessments
- **H5P Content:** Interactive content
- **SCORM Package:** External packages

**Customizing Content Types:**

For each content type, configure:

1. **Edit tab:**
   - Name and description
   - Submission form settings
   - Publishing options
   - Display settings

2. **Manage fields tab:**
   - Add/remove/edit fields
   - Field types and settings
   - Field validation

3. **Manage display tab:**
   - Field display settings
   - Field formatter
   - Field order

4. **Manage form display tab:**
   - Form widget selection
   - Field order on forms
   - Required/optional fields

### Text Formats

Navigate to: **Configuration → Content authoring → Text formats and editors**

**Configured Formats:**

1. **Full HTML:**
   - For administrators
   - All HTML tags allowed
   - Complete CKEditor toolbar
   - Image upload enabled

2. **Basic HTML:**
   - For content creators
   - Safe HTML tags only
   - Standard formatting
   - Image embed capability

3. **Restricted HTML:**
   - For end users
   - Minimal HTML
   - Comments and forums

**Customizing CKEditor:**

Edit a text format → "CKEditor settings"

Configure:
- **Toolbar:** Drag buttons to customize
- **Plugins:** Enable additional plugins
- **Image uploads:** Size limits and destination
- **Styles:** Custom CSS classes
- **Media embed:** Settings for embedded content

### Image Styles

Navigate to: **Configuration → Media → Image styles**

**Pre-configured Styles:**
- **catalog_thumb:** Catalog thumbnails
- **learning_path_thumbnail:** Learning path images
- **user_picture:** User avatars
- **training_list_item:** Course listing images

**Creating Custom Image Style:**

1. Click "Add image style"
2. Enter style name (e.g., "hero_image")
3. Add effects:
   - Scale: Proportional resize
   - Crop: Fixed aspect ratio
   - Rotate
   - Desaturate
4. Save

**Common Image Sizes:**
- Hero banner: 1920×600px
- Course thumbnail: 400×300px
- User avatar: 150×150px
- Card image: 350×200px

## Learning Path Configuration

### Opigno Settings

Navigate to: **Configuration → Opigno**

#### Dashboard Settings

**Configuration → Opigno → Dashboard settings**

Enable/disable widgets:
- ✓ Learning path progress
- ✓ Latest active trainings
- ✓ Recent activity
- ✓ Upcoming events
- ✓ Achievements
- ✓ Messages
- ✓ Forum latest posts

**Widget Layout:**
- Default columns: 2 or 3
- Allow user customization: Yes/No
- Default widget placement

#### Module Settings

**Configuration → Opigno → Module settings**

Configure:
- **Default passing score:** 70% (or customize)
- **Allow backwards navigation:** Yes/No
- **Allow reattempt:** Yes/No
- **Number of attempts:** Unlimited or specific number
- **Randomize activities:** Yes/No
- **Show activity navigation:** Yes/No
- **Activity time restriction:** Enable/disable

#### Certificate Settings

**Configuration → Opigno → Certificate settings**

1. **Create Certificate Templates:**
   - Template name
   - HTML/CSS design
   - Dynamic tokens:
     - `[user:display-name]` - User's name
     - `[opigno:training-name]` - Course name
     - `[date:custom:Y-m-d]` - Completion date
     - `[opigno:score]` - Final score

2. **Certificate Options:**
   - PDF orientation (portrait/landscape)
   - Paper size (A4, Letter)
   - Include QR code for verification
   - Expiration date rules

**Example Certificate Template:**
```html
<div class="certificate">
  <h1>Certificate of Completion</h1>
  <p>This certifies that</p>
  <h2>[user:display-name]</h2>
  <p>has successfully completed</p>
  <h2>[opigno:training-name]</h2>
  <p>with a score of [opigno:score]%</p>
  <p>Completed on [date:custom:F j, Y]</p>
  <div class="signature">
    <p>___________________________</p>
    <p>Training Director</p>
  </div>
</div>

<style>
.certificate {
  text-align: center;
  padding: 50px;
  font-family: 'Times New Roman', serif;
}
h1 { font-size: 36pt; color: #0066cc; }
h2 { font-size: 24pt; font-weight: bold; }
</style>
```

#### Catalog Settings

**Configuration → Opigno → Catalog settings**

Configure training catalog:
- **Catalog view mode:** Grid or list
- **Items per page:** 12, 24, 48
- **Sorting options:** Title, date, popularity
- **Filtering:** By category, skills, duration
- **Access control:** Public or authenticated only

### Skills Configuration

Navigate to: **Configuration → Opigno → Skills**

**Creating Skill Taxonomy:**

1. Click "Add skill"
2. Enter skill name (e.g., "Project Management")
3. Add description
4. Set skill level (optional)
5. Create hierarchy:
   - Parent skills
   - Child skills
6. Save

**Associating Skills with Content:**

When creating learning paths or modules:
- Select relevant skills from taxonomy
- Set target skill level
- Configure prerequisite skills

**Skill Tracking:**

Users can view their skill progress:
- Current skill level
- Required skills for courses
- Skill gaps
- Recommended training

## Performance Configuration

### Caching

Navigate to: **Configuration → Development → Performance**

**Production Settings:**

1. **Caching:**
   - ✓ Cache pages for anonymous users
   - ✓ Cache blocks
   - Cache maximum age: 1 hour (3600 seconds)

2. **Bandwidth Optimization:**
   - ✓ Aggregate CSS files
   - ✓ Aggregate JavaScript files

**Development Settings:**

1. **Caching:**
   - ☐ Disable all caching for development
   - Cache maximum age: No caching

2. **Bandwidth Optimization:**
   - ☐ Disable aggregation for debugging

**Advanced Caching (Redis):**

Install Redis for better performance:

```bash
# Install Redis module
composer require drupal/redis

# Enable module
drush en redis -y
```

Configure in `settings.php`:
```php
// Redis configuration
$settings['redis.connection']['interface'] = 'PhpRedis';
$settings['redis.connection']['host'] = '127.0.0.1';
$settings['redis.connection']['port'] = 6379;
$settings['cache']['default'] = 'cache.backend.redis';
```

### Database Optimization

**Regular Maintenance:**

```bash
# Clear cache
drush cache:rebuild

# Clear old watchdog entries
drush watchdog:delete all

# Optimize tables (MySQL)
drush sql:query "OPTIMIZE TABLE node, users, cache_menu"
```

**Configure Cron:**

Navigate to: **Configuration → System → Cron**

- **Run cron every:** 3 hours (recommended)
- Or use system cron (recommended for production)

### Image Optimization

Navigate to: **Configuration → Media → Image toolkit**

**GD Toolkit Settings:**
- JPEG quality: 85% (balance quality/size)
- PNG compression: Medium

**Install ImageMagick (Recommended):**

```bash
composer require drupal/imagemagick
drush en imagemagick -y
```

Configure at: **Configuration → Media → Image toolkit**

## Security Configuration

### Secure Password Reset

Navigate to: **Configuration → People → Account settings**

Ensure:
- ✓ Enable password recovery via email
- ✓ Require email verification for new accounts
- Set password reset timeout: 24 hours

### User Protection

Navigate to: **Configuration → People → User protection**

Configure protections:
- ✓ Protect email changes
- ✓ Protect password changes
- ✓ Protect role changes
- ✓ Protect user deletion
- ✓ Protect username changes

### File Upload Security

Navigate to: **Configuration → Media → File system**

**Allowed Extensions:**

For each upload field:
- Documents: `txt pdf doc docx xls xlsx ppt pptx`
- Images: `png jpg jpeg gif`
- Video: `mp4 webm ogv`
- Audio: `mp3 wav ogg`

**Prevent PHP Uploads:** Never allow `php php3 php4 php5 phtml`

**File Size Limits:**

Set reasonable limits:
- User pictures: 2 MB
- Course documents: 50 MB
- Videos: 500 MB
- H5P packages: 100 MB

Configure in PHP `php.ini`:
```ini
upload_max_filesize = 500M
post_max_size = 500M
```

### HTTPS Configuration

**Force HTTPS in settings.php:**

```php
// Force HTTPS
if (isset($_SERVER['HTTP_X_FORWARDED_PROTO'])
    && $_SERVER['HTTP_X_FORWARDED_PROTO'] == 'https') {
  $_SERVER['HTTPS'] = 'on';
}

// Force HTTPS redirect
$settings['reverse_proxy'] = TRUE;
$settings['reverse_proxy_addresses'] = ['127.0.0.1'];
```

**Or use .htaccess (Apache):**

```apache
# Force HTTPS
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}/$1 [R=301,L]
```

### Security Headers

Add to web server configuration:

**Apache (.htaccess):**
```apache
Header set X-Content-Type-Options "nosniff"
Header set X-Frame-Options "SAMEORIGIN"
Header set X-XSS-Protection "1; mode=block"
Header set Referrer-Policy "strict-origin-when-cross-origin"
```

**Nginx:**
```nginx
add_header X-Content-Type-Options "nosniff" always;
add_header X-Frame-Options "SAMEORIGIN" always;
add_header X-XSS-Protection "1; mode=block" always;
add_header Referrer-Policy "strict-origin-when-cross-origin" always;
```

## Integration Configuration

### Tin Can API / xAPI

Navigate to: **Configuration → Opigno → Tin Can settings**

**Connecting to LRS:**

1. **LRS Endpoint:** Enter your LRS URL
   ```
   https://lrs.example.com/xapi/
   ```

2. **Authentication:**
   - Username: Your LRS username
   - Password: Your LRS password
   - Or use API key authentication

3. **Test Connection:** Click "Test" to verify

4. **Enable Tracking:** Check activities to track
   - Course launched
   - Course completed
   - Quiz attempted
   - Quiz passed
   - Video watched
   - Document viewed

**Popular LRS Providers:**
- Learning Locker
- Watershed
- Veracity Learning
- SCORM Cloud

### Email Configuration

Navigate to: **Configuration → System → Mail System**

**SMTP Configuration (Recommended):**

Install SMTP module:
```bash
composer require drupal/smtp
drush en smtp -y
```

Configure at: **Configuration → System → SMTP Authentication Support**

Settings:
- SMTP server: `smtp.gmail.com` (or your provider)
- SMTP port: `587` (TLS) or `465` (SSL)
- Username: Your email address
- Password: Your email password or app password
- From address: `no-reply@yoursite.com`
- From name: "Acme Learning Platform"

**Test Email:** Send test email to verify configuration.

### Social Login (Optional)

**Enable OAuth/Social Login:**

```bash
composer require drupal/social_auth_google
composer require drupal/social_auth_facebook
drush en social_auth_google social_auth_facebook -y
```

Configure at: **Configuration → People → Social Auth**

## Backup Configuration

### Automated Backups

**Install Backup & Migrate:**

```bash
composer require drupal/backup_migrate
drush en backup_migrate -y
```

**Configure Backups:**

Navigate to: **Configuration → Development → Backup and Migrate**

1. **Create Backup Schedule:**
   - Frequency: Daily at 2:00 AM
   - Retain: 7 daily, 4 weekly
   - Backup destination: Private files or off-site

2. **What to Backup:**
   - ✓ Database
   - ✓ Public files
   - ✓ Private files
   - ☐ Code (use Git instead)

3. **Notifications:**
   - Email on success: No (too frequent)
   - Email on failure: Yes

### Manual Backup

**Database:**
```bash
drush sql:dump --gzip --result-file=backup-$(date +%Y%m%d).sql.gz
```

**Files:**
```bash
tar -czf files-backup-$(date +%Y%m%d).tar.gz web/sites/default/files
tar -czf private-files-backup-$(date +%Y%m%d).tar.gz /var/www/private_files
```

**Configuration:**
```bash
drush config:export
tar -czf config-backup-$(date +%Y%m%d).tar.gz config/
```

## Troubleshooting Configuration Issues

### Configuration Not Saving

**Symptoms:** Changes revert after saving

**Solutions:**
1. Check file permissions: `chmod 755 web/sites/default`
2. Verify database connection in settings.php
3. Clear cache: `drush cache:rebuild`
4. Check for configuration overrides in settings.php
5. Review PHP error logs

### Permission Denied

**Symptoms:** Cannot access configuration pages

**Solutions:**
1. Verify user role has permissions
2. Check **People → Permissions**
3. Clear cache: `drush cache:rebuild`
4. Log in as user 1 (admin) to verify

### Performance Issues After Configuration

**Symptoms:** Slow page loads, timeouts

**Solutions:**
1. Enable caching: **Configuration → Performance**
2. Enable CSS/JS aggregation
3. Increase PHP memory limit in php.ini
4. Add database indexes if needed
5. Consider Redis/Memcache
6. Check for slow query log in database

## Best Practices

1. **Document Changes:** Keep notes on configuration modifications
2. **Version Control:** Export and commit config changes
3. **Test First:** Test configuration in development environment
4. **Backup Before:** Always backup before major changes
5. **Review Logs:** Check watchdog logs after configuration
6. **Performance Test:** Monitor performance after changes
7. **Security Review:** Regular security audits
8. **Update Regularly:** Keep Drupal and modules updated

## Additional Resources

- **Drupal Configuration Management:** https://www.drupal.org/docs/configuration-management
- **Opigno Documentation:** https://opigno.org/documentation
- **Drupal Security:** https://www.drupal.org/security

## Next Steps

- **[Installation Guide](INSTALLATION.md)** - Initial setup
- **[Theme Guide](THEME.md)** - Customize appearance
- **[Features Guide](FEATURES.md)** - Explore capabilities

---

**Version:** 1.0.1 | **Last Updated:** 2025-11-10
