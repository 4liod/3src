# Aristotle Theme Documentation

The **Aristotle theme** is the responsive, modern interface for the Cloud3src LMS distribution. This guide covers configuration, customization, and best practices for working with the theme.

## Table of Contents

- [Overview](#overview)
- [Theme Features](#theme-features)
- [Configuration](#configuration)
- [Customization](#customization)
- [Asset Management](#asset-management)
- [Troubleshooting](#troubleshooting)

## Overview

**Theme Name:** Aristotle
**Version:** ~3.2.0
**Type:** Contributed Drupal theme
**Project Page:** https://www.drupal.org/project/aristotle
**License:** GPL-2.0+

Aristotle is specifically designed for learning management systems built on Opigno. It provides:

- Responsive, mobile-first design
- Customizable branding and colors
- Homepage slideshow capabilities
- Flexible menu configuration
- Optimized for learning content display
- Mobile app integration support

## Theme Features

### Responsive Design

- **Mobile-First:** Optimized for phones, tablets, and desktops
- **Breakpoints:** Adapts to all screen sizes automatically
- **Touch-Friendly:** Large touch targets for mobile users
- **Progressive Enhancement:** Works on all browsers

### Learning-Focused Layout

- **Clean Content Display:** Distraction-free learning experience
- **Course Navigation:** Easy-to-use course structure navigation
- **Dashboard Widgets:** Customizable learning dashboard
- **Progress Tracking:** Visual progress indicators
- **Forum Integration:** Dedicated forum layouts

### Branding Options

- **Custom Logos:** Upload your organization's branding
- **Color Schemes:** Customizable color palette
- **Login Page:** Branded login experience
- **Header Images:** Optional header background images
- **Favicon:** Custom site icon

## Configuration

### Accessing Theme Settings

Navigate to: **Administration → Appearance → Settings → Aristotle**

Or directly: `/admin/appearance/settings/aristotle`

### Configuration Options

#### 1. Logo Settings

**Default Configuration:**
```yaml
logo:
  path: themes/aristotle/assets/4LIOD.svg
  use_default: 0
logo_path_anonymous: 4LIOD-white.svg
```

**How to Configure:**

1. **Standard Logo** (for authenticated users):
   - Navigate to: **Administration → Appearance → Settings → Aristotle**
   - Scroll to "Logo image settings"
   - Uncheck "Use the default logo supplied by the theme"
   - Upload your logo or enter path: `themes/aristotle/assets/your-logo.svg`
   - Recommended format: SVG or PNG with transparency
   - Recommended size: 200px width, auto height

2. **Anonymous User Logo** (for login page):
   - Set in theme settings under "Anonymous Logo"
   - File path: `4LIOD-white.svg` (relative to theme assets)
   - Usually a white/light version for dark backgrounds
   - Same format/size recommendations as standard logo

**File Location:**
```
web/themes/contrib/aristotle/assets/
├── 4LIOD.svg                    # Standard logo
├── 4LIOD-white.svg              # Anonymous/login logo
└── 4LIOD-login-image.jpg        # Login background
```

#### 2. Homepage Settings

**Default Configuration:**
```yaml
aristotle_home_page_settings:
  aristotle_use_home_page_markup: 1
  aristotle_home_page_slides:
    1:
      aristotle_home_page_image_path: 4LIOD-login-image.jpg
      aristotle_home_page_image_upload: {}
    actions: {}
```

**How to Configure:**

1. Navigate to theme settings
2. Find "Homepage Settings" section
3. Enable "Use home page markup"
4. Configure slideshow images:
   - **Add Slide:** Upload image or specify path
   - **Slide Title:** Optional heading text
   - **Slide Description:** Optional description text
   - **Link URL:** Optional call-to-action link

**Slideshow Best Practices:**
- Image size: 1920×1080px or larger
- Format: JPG for photos, PNG for graphics
- File size: Keep under 500KB for performance
- Alt text: Always provide descriptive alt text

**Using the Included Login Image:**

The distribution includes a pre-configured login background image:
```
images/3src_Image_connexion_1600-829_2.jpg
```

To use it:
```bash
cp images/3src_Image_connexion_1600-829_2.jpg web/themes/contrib/aristotle/assets/4LIOD-login-image.jpg
```

#### 3. Menu Configuration

**Default Configuration:**
```yaml
aristotle_menu_source: main
aristotle_menu_show_for_anonymous: 1
```

**How to Configure:**

1. **Menu Source:**
   - Default: "main" (Main navigation menu)
   - Options: Any configured Drupal menu
   - Change in: Theme settings → "Menu settings"

2. **Anonymous User Visibility:**
   - `aristotle_menu_show_for_anonymous: 1` - Menu visible to logged-out users
   - `aristotle_menu_show_for_anonymous: 0` - Menu hidden for anonymous users
   - Useful for restricting navigation before login

**Editing Menu Items:**

Navigate to: **Administration → Structure → Menus → Main navigation**

Pre-configured menu items:
- Home (weight: -10)
- Catalogue (weight: -9)
- Calendar (weight: -7)
- Statistics (weight: -5)

#### 4. Header Background Image

**Default Configuration:**
```yaml
aristotle_use_header_background: 0
aristotle_header_image_path: ''
aristotle_header_image_upload: {}
```

**How to Enable:**

1. Navigate to theme settings
2. Find "Header Background Image" section
3. Check "Use header background image"
4. Upload image or specify path
5. Save configuration

**Recommendations:**
- Size: 1920×400px
- Format: JPG or PNG
- Style: Subtle, low-contrast for text readability
- File size: Under 200KB

#### 5. User Picture Settings

**Default Configuration:**
```yaml
features:
  node_user_picture: 0         # Disabled for content
  comment_user_picture: 1      # Enabled for comments
  comment_user_verification: 1
  favicon: 1
```

**Comment User Pictures:**
- Displays user avatars next to comments
- Enhances social learning experience
- Configured in: Theme settings → "User pictures"

**User Picture Configuration:**

Navigate to: **Administration → Configuration → People → Account settings**
- Field management for user pictures
- Image style configuration
- Default avatar settings

#### 6. Favicon

**Default Configuration:**
```yaml
favicon:
  use_default: 1
```

**How to Customize:**

1. Navigate to theme settings
2. Find "Favicon" section
3. Uncheck "Use the default favicon"
4. Upload your custom favicon
5. Recommended: 32×32px or 64×64px PNG/ICO

#### 7. Mobile App Settings

**Default Configuration:**
```yaml
mobile_app_premium_logo: 0
browser_sync: 0
```

**Mobile App Premium Logo:**
- Enable for Opigno mobile app integration
- Requires Opigno Mobile App module
- Shows premium branding in mobile app

**Browser Sync:**
- Development feature for live CSS reloading
- Keep disabled in production
- Useful for theme development

## Customization

### Custom CSS

#### Method 1: Theme Sub-theme (Recommended)

Create a custom sub-theme for extensive customizations:

```bash
# Create sub-theme directory
mkdir -p web/themes/custom/mytheme
```

**mytheme.info.yml:**
```yaml
name: My Custom Theme
type: theme
description: Custom sub-theme of Aristotle
core_version_requirement: ^9 || ^10
base theme: aristotle

libraries:
  - mytheme/global-styling

regions:
  header: Header
  primary_menu: 'Primary menu'
  content: Content
  sidebar_first: 'Sidebar first'
  footer: Footer
```

**mytheme.libraries.yml:**
```yaml
global-styling:
  version: 1.0
  css:
    theme:
      css/custom.css: {}
  js:
    js/custom.js: {}
```

**css/custom.css:**
```css
/* Your custom styles */
:root {
  --primary-color: #0066cc;
  --secondary-color: #333333;
}

.header-logo {
  max-width: 220px;
}

/* Customize button styles */
.btn-primary {
  background-color: var(--primary-color);
  border-radius: 4px;
}
```

#### Method 2: CSS Injector Module

For simple CSS tweaks without creating a sub-theme:

1. Install CSS Injector module: `composer require drupal/css_injector`
2. Enable: `drush en css_injector -y`
3. Navigate to: **Administration → Configuration → Development → CSS Injector**
4. Add custom CSS rules

### Custom Templates

Override Aristotle templates in your sub-theme:

```
web/themes/custom/mytheme/
└── templates/
    ├── page.html.twig           # Page layout
    ├── node.html.twig            # Content display
    ├── block.html.twig           # Block layout
    └── user/
        └── user-picture.html.twig # User avatars
```

Copy templates from Aristotle to customize:
```bash
cp web/themes/contrib/aristotle/templates/page.html.twig \
   web/themes/custom/mytheme/templates/
```

### Color Scheme Customization

Aristotle uses CSS variables for easy color customization:

```css
/* Custom color scheme in your sub-theme */
:root {
  /* Primary colors */
  --color-primary: #0066cc;
  --color-primary-dark: #004c99;
  --color-primary-light: #3399ff;

  /* Accent colors */
  --color-accent: #ff6600;
  --color-success: #28a745;
  --color-warning: #ffc107;
  --color-danger: #dc3545;

  /* Neutrals */
  --color-text: #333333;
  --color-background: #ffffff;
  --color-border: #dee2e6;

  /* Learning-specific */
  --color-progress: #28a745;
  --color-course: #0066cc;
  --color-certificate: #ffc107;
}
```

### Typography

Customize fonts in your sub-theme CSS:

```css
/* Import Google Fonts */
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;600;700&display=swap');

body {
  font-family: 'Open Sans', 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  line-height: 1.6;
  color: var(--color-text);
}

h1, h2, h3, h4, h5, h6 {
  font-weight: 600;
  line-height: 1.2;
}

h1 { font-size: 2.5rem; }
h2 { font-size: 2rem; }
h3 { font-size: 1.75rem; }
```

## Asset Management

### Recommended Asset Organization

```
web/themes/contrib/aristotle/assets/
├── logos/
│   ├── logo-standard.svg        # Main logo
│   ├── logo-white.svg           # Light background logo
│   └── favicon.png              # Site icon
├── images/
│   ├── login-background.jpg     # Login page background
│   ├── homepage-slide-1.jpg     # Homepage slideshow
│   ├── homepage-slide-2.jpg
│   └── header-background.jpg    # Optional header image
└── branding/
    └── brand-colors.txt         # Document your color scheme
```

### Image Optimization

Before uploading images:

1. **Resize to appropriate dimensions**
2. **Optimize file size:**
   - Use tools like TinyPNG, ImageOptim
   - Target: Under 300KB for large images
   - Target: Under 100KB for thumbnails

3. **Use appropriate formats:**
   - JPG for photographs
   - PNG for graphics with transparency
   - SVG for logos and icons

### Asset Deployment

**Development:**
```bash
# Copy assets during theme setup
cp -r branding/logos/* web/themes/contrib/aristotle/assets/
```

**Production:**
- Include assets in version control
- Or deploy via CI/CD pipeline
- Or upload via Drupal file management UI

## Troubleshooting

### Logo Not Appearing

**Symptoms:** Logo missing or broken image icon

**Solutions:**
1. Verify file path in theme settings
2. Check file permissions: `chmod 644 web/themes/contrib/aristotle/assets/4LIOD.svg`
3. Clear Drupal cache: `drush cache:rebuild`
4. Verify file exists: `ls -l web/themes/contrib/aristotle/assets/`

### Slideshow Not Working

**Symptoms:** Homepage slideshow not displaying or not advancing

**Solutions:**
1. Verify "Use home page markup" is enabled in theme settings
2. Check that slide images are uploaded or paths are correct
3. Clear cache: `drush cache:rebuild`
4. Check browser console for JavaScript errors
5. Verify slick library is loaded: Check page source for slick.js

### Custom CSS Not Applying

**Symptoms:** Custom styles not visible on site

**Solutions:**
1. Clear Drupal cache: `drush cache:rebuild`
2. Clear browser cache: Ctrl+Shift+R (hard refresh)
3. Check CSS aggregation: **Configuration → Performance**
4. Verify library is attached in .info.yml
5. Check CSS file permissions: `chmod 644 css/custom.css`

### Mobile Display Issues

**Symptoms:** Site not responsive on mobile devices

**Solutions:**
1. Verify viewport meta tag is present
2. Clear cache: `drush cache:rebuild`
3. Test with browser dev tools mobile emulation
4. Check for CSS overrides breaking responsive styles
5. Verify no JavaScript errors in console

### Theme Settings Not Saving

**Symptoms:** Changes revert after saving

**Solutions:**
1. Check file permissions on configuration directory
2. Verify database connection
3. Check for PHP errors in logs
4. Clear cache and try again
5. Check for configuration overrides in settings.php

## Best Practices

### Performance

1. **Optimize Images:** Compress before uploading
2. **Enable Aggregation:** CSS/JS aggregation in production
3. **Use SVG for Logos:** Scalable and small file size
4. **Limit Slideshow Slides:** 3-5 slides maximum
5. **Enable Caching:** Configure Drupal cache settings

### Accessibility

1. **Alt Text:** Always provide for images
2. **Color Contrast:** Maintain WCAG AA standards (4.5:1 minimum)
3. **Keyboard Navigation:** Test all interactive elements
4. **Screen Reader Testing:** Use NVDA or JAWS
5. **Semantic HTML:** Use proper heading hierarchy

### Branding Consistency

1. **Document Colors:** Keep brand color palette documented
2. **Logo Versions:** Maintain multiple logo variations
3. **Typography:** Use consistent font families
4. **Spacing:** Maintain consistent margins and padding
5. **Style Guide:** Create a living style guide document

### Development Workflow

1. **Use Sub-theme:** Never modify Aristotle directly
2. **Version Control:** Track custom theme in Git
3. **Test Responsive:** Check all breakpoints
4. **Cross-browser:** Test Chrome, Firefox, Safari, Edge
5. **Documentation:** Document custom changes

## Additional Resources

- **Aristotle Theme Project:** https://www.drupal.org/project/aristotle
- **Drupal Theming Guide:** https://www.drupal.org/docs/theming-drupal
- **Twig Templates:** https://www.drupal.org/docs/theming-drupal/twig-in-drupal
- **Opigno Themes:** https://opigno.org/themes

## Next Steps

- **[Configure LMS Features →](FEATURES.md)**
- **[Customize Configuration →](CONFIGURATION.md)**
- **[View Installation Guide →](INSTALLATION.md)**

---

**Theme Version:** ~3.2.0 | **Last Updated:** 2025-11-10
