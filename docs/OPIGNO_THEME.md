# Opigno Theme Integration - Cloud3src

This document details all Opigno LMS-specific theme configurations, blocks, and integrations with the Aristotle theme.

**Distribution Version:** 1.0.1
**Theme:** Aristotle ~3.2.0
**Opigno Version:** 3.2.0
**Generated:** 2025-11-10

---

## Table of Contents

- [Overview](#overview)
- [Theme Configuration](#theme-configuration)
- [Opigno Dashboard Settings](#opigno-dashboard-settings)
- [Opigno-Specific Blocks](#opigno-specific-blocks)
- [Theme Regions](#theme-regions)
- [Opigno Menu Structure](#opigno-menu-structure)
- [Block Visibility Rules](#block-visibility-rules)
- [Integration Points](#integration-points)

---

## Overview

The Cloud3src distribution uses the **Aristotle theme** as both the default frontend theme and admin theme. Aristotle is specifically designed for Opigno LMS and includes specialized regions, blocks, and styling for learning management features.

**Key Integration Points:**

- Dashboard widgets and layouts
- Learning path navigation blocks
- Calendar integration
- Notification system
- Course catalog filters
- Admin menu integration
- Mobile app support

---

## Theme Configuration

### Active Themes

**Configuration File:** `config/install/system.theme.yml`

```yaml
default: aristotle    # Frontend theme for learners
admin: aristotle      # Admin theme for administrators
```

**Implementation:**
- **Unified Experience:** Same theme for both frontend and backend provides consistent UX
- **LMS-Optimized:** Aristotle includes Opigno-specific styling and components
- **Responsive:** Mobile-first design for learners on all devices

### Theme Dependencies

**Modules depending on Aristotle theme:**

1. **Opigno Dashboard** - Dashboard layout and widgets
2. **Opigno Learning Path** - Learning path navigation
3. **System Blocks** - Core Drupal blocks adapted for LMS
4. **Views Blocks** - Custom Opigno views integrated into theme

---

## Opigno Dashboard Settings

**Configuration File:** `config/install/opigno_dashboard.settings.yml`

### Dashboard Theme Binding

```yaml
theme: aristotle
```

**Line:** 323

The dashboard is explicitly bound to the Aristotle theme, ensuring all dashboard widgets render with proper LMS styling.

### Available Dashboard Widgets

**Enabled Widgets (available: '1'):**

| Widget ID | Purpose | Mandatory |
|-----------|---------|-----------|
| `opigno_user_stats_block` | User learning statistics | No |
| `opigno_social_wall_block` | Social activity feed | No |
| `opigno_user_connections_block` | User network/connections | No |
| `views_block:latest_active_trainings-block` | Recently accessed courses | No |
| `views_block:opigno_calendar-month_block` | Monthly calendar view | No |
| `views_block:opigno_group_members-block_pending` | Pending group members | No |
| `views_block:opigno_score_modules-dashboard_notavaluated_modules` | Unevaluated modules | No |
| `views_block:private_message-block_dashboard` | Private messages | No |
| `views_block:who_s_new-block_1` | New users | No |
| `views_block:who_s_online-who_s_online_block` | Online users | No |

**Total Available Widgets:** 10 core widgets + 90+ disabled entity/system widgets

### Widget Customization

Users can customize their dashboard by:
- Enabling/disabling available widgets
- Rearranging widget order
- Choosing single or multi-column layout

Administrators control which widgets are available via the dashboard settings configuration.

---

## Opigno-Specific Blocks

### 1. Opigno Admin Menu Block

**Configuration File:** `config/install/block.block.opigno_admin.yml`

**Block Details:**
```yaml
id: opigno_admin
theme: aristotle
region: admin_opigno      # Special Opigno admin region
weight: 0
plugin: 'system_menu_block:opigno-admin'
```

**Purpose:**
- Admin navigation menu for Opigno settings
- Quick access to LMS configuration
- Separate from standard Drupal admin menu

**Menu Items:**
- Dashboard management
- Menu management
- Graphical settings (theme)
- Global settings

**Region:** `admin_opigno` (Aristotle theme's special admin region)

---

### 2. Training Catalog Filter Block

**Configuration File:** `config/install/block.block.opigno_training_catalog_filter.yml`

**Block Details:**
```yaml
id: opigno_training_catalog_filter
theme: aristotle
region: sidebar_first
weight: 0
plugin: 'views_exposed_filter_block:opigno_training_catalog-training_catalogue'
```

**Purpose:**
- Filter/search interface for course catalog
- Sidebar placement for easy access
- Integrated with training catalog view

**Features:**
- Filter by category
- Search by keywords
- Filter by skills
- Filter by duration

**Location:** Left sidebar on catalog pages

---

### 3. Learning Path Steps Block

**Configuration File:** `config/optional/block.block.lp_steps_block.yml`

**Block Details:**
```yaml
id: lp_steps_block
theme: aristotle
region: sidebar_first
weight: 0
plugin: lp_steps_block
```

**Purpose:**
- Navigation within learning paths
- Shows current progress
- Lists all steps/modules in path

**Visibility Rules:**
```yaml
visibility:
  request_path:
    pages: "/module/*/result/*\r\n/group/*/module/*"
    negate: false
```

**Displays on:**
- Module result pages
- Module activity pages within groups
- Learning path navigation contexts

**Provider:** `opigno_learning_path` module

---

### 4. Opigno Calendar Block

**Configuration File:** `config/optional/block.block.views_block__opigno_calendar_month_block.yml`

**Block Details:**
```yaml
id: views_block__opigno_calendar_month_block
theme: aristotle
region: content
weight: 0
plugin: 'views_block:opigno_calendar-month_block'
```

**Purpose:**
- Monthly calendar view
- Display upcoming events
- ILT (Instructor-Led Training) schedules
- Course deadlines

**Multiple Configurations:**

1. **Standalone Calendar Block**
   - File: `block.block.views_block__opigno_calendar_month_block.yml`
   - Region: content
   - Full calendar page

2. **Dashboard Calendar Widget**
   - File: `block.block.dashboard_views_block_opigno_calendar_month_block.yml`
   - Region: content
   - Dashboard widget version

---

### 5. Opigno Notifications Block

**Configuration File:** `config/optional/block.block.dashboard_views_block_opigno_notifications_block_unread_dashboard.yml`

**Block Details:**
```yaml
id: dashboard_views_block_opigno_notifications_block_unread_dashboard
theme: aristotle
region: content
weight: 0
plugin: 'views_block:opigno_notifications-block_unread_dashboard'
```

**Purpose:**
- Display unread notifications
- Dashboard widget
- Learning activity alerts
- System notifications

**Notification Types:**
- New course assignments
- Approaching deadlines
- Certificate awards
- Forum replies
- Private messages

---

### 6. Opigno Group Members Block

**Configuration File:** `config/optional/block.block.dashboard_views_block_opigno_group_members_block_pending.yml`

**Block Details:**
```yaml
id: dashboard_views_block_opigno_group_members_block_pending
theme: aristotle
region: content
weight: 0
plugin: 'views_block:opigno_group_members-block_pending'
```

**Purpose:**
- Display pending group membership requests
- Group manager dashboard widget
- Member approval interface

**Visible to:**
- Group administrators
- Student managers
- Users with group management permissions

---

### 7. Opigno Score Modules Block

**Configuration File:** `config/optional/block.block.dashboard_views_block_opigno_score_modules_dashboard_notavaluated_modules.yml`

**Block Details:**
```yaml
id: dashboard_views_block_opigno_score_modules_dashboard_notavaluated_modules
theme: aristotle
region: content
weight: 0
plugin: 'views_block:opigno_score_modules-dashboard_notavaluated_modules'
```

**Purpose:**
- Display modules awaiting evaluation
- Instructor/grader dashboard widget
- Manual grading queue

**Features:**
- Lists unevaluated submissions
- Links to grading interface
- Priority indicators
- Submission timestamps

---

## Theme Regions

### Aristotle Theme Regions Used by Opigno

| Region Name | Machine Name | Opigno Usage | Blocks |
|-------------|--------------|--------------|--------|
| **Branding** | `branding` | Site logo and branding | Site Branding |
| **Menu** | `menu` | Main navigation | Main Navigation |
| **Admin Opigno** | `admin_opigno` | Opigno admin menu | Opigno Admin Menu |
| **Sidebar First** | `sidebar_first` | Course navigation & filters | Catalog Filter, LP Steps |
| **Content** | `content` | Main content & dashboard widgets | Calendar, Notifications, Scores, Primary Actions, Tabs |
| **Footer** | `footer` | Site footer | Site Branding (secondary) |

### Special Opigno Region

**`admin_opigno`** is a unique region in the Aristotle theme specifically for Opigno administrative functions:

- Only visible to users with admin permissions
- Contains Opigno-specific admin menu
- Separate from standard Drupal admin toolbar
- Quick access to LMS configuration

---

## Opigno Menu Structure

### Opigno Admin Menu

**Configuration File:** `config/install/system.menu.opigno-admin.yml`

**Menu Details:**
```yaml
id: opigno-admin
label: 'opigno admin'
description: ''
locked: false
```

**Menu Structure:**

Referenced in `cloud3src.links.menu.yml`:

```yaml
# Dashboard management
opigno.dashboard.admin:
  title: 'Dashboard'
  route_name: opigno_dashboard.settings_form
  parent: system.admin

# Menu management
opigno.menu.admin:
  title: 'Menu'
  route_name: entity.menu.collection
  parent: system.admin

# Theme settings
opigno.graphical.admin:
  title: 'Graphical settings'
  route_name: system.themes_page
  parent: system.admin

# Global settings
opigno.global.admin:
  title: 'Global settings'
  route_name: system.admin_config
  parent: system.admin
```

**Purpose:**
- Streamlined LMS administration
- Quick access to common tasks
- Organized by function
- Optimized for training managers

---

## Block Visibility Rules

### Path-Based Visibility

#### Learning Path Steps Block

**Visible on:**
```
/module/*/result/*
/group/*/module/*
```

**Context:**
- Module result pages (after completing activities)
- Module pages within learning paths
- Provides contextual navigation

**Logic:**
- Shows current position in learning path
- Lists completed and upcoming modules
- Progress indicators
- Next/previous navigation

### Role-Based Visibility

While not explicitly configured in the provided files, Opigno blocks typically respect:

- **Student Manager:** Group member blocks, statistics
- **Administrator:** All admin blocks and widgets
- **Authenticated User:** Dashboard widgets based on permissions
- **Anonymous User:** No Opigno blocks visible

---

## Integration Points

### 1. Dashboard Integration

**How Opigno integrates with Aristotle:**

```yaml
# opigno_dashboard.settings.yml line 323
theme: aristotle
```

- Dashboard renders using Aristotle theme templates
- Widgets styled with Aristotle CSS
- Responsive layout for mobile learners
- Customizable widget placement

**Dashboard Features:**
- Drag-and-drop widget organization
- Multi-column layouts
- Widget enable/disable per user
- Default widget configurations

### 2. Block System Integration

**Aristotle's block regions used:**

```
branding           → Site identity
menu               → Main navigation
admin_opigno       → LMS admin menu
sidebar_first      → Course navigation
content            → Dashboard & main content
footer             → Site footer
```

**Block Placement Strategy:**
- Critical navigation in sidebar
- Dashboard widgets in content area
- Admin tools in dedicated region
- Responsive stacking on mobile

### 3. Views Integration

**Opigno Views Blocks:**

All Opigno views blocks integrate seamlessly with Aristotle:

- `opigno_calendar-month_block` - Calendar widget
- `opigno_notifications-block_unread_dashboard` - Notifications
- `opigno_group_members-block_pending` - Group management
- `opigno_score_modules-dashboard_notavaluated_modules` - Grading queue
- `latest_active_trainings-block` - Recent courses
- `private_message-block_dashboard` - Messaging

**Styling:**
- Views templates use Aristotle CSS classes
- Responsive tables and lists
- Icon integration
- Accessibility compliant

### 4. Menu System Integration

**Menus managed through Aristotle:**

1. **Main Navigation** (`main`)
   - Home, Catalogue, Calendar, Statistics
   - Configurable visibility for anonymous users
   - Responsive mobile menu

2. **Opigno Admin Menu** (`opigno-admin`)
   - Dashboard, Menu, Settings, Configuration
   - Quick admin access
   - Context-sensitive items

3. **Account Menu** (`account`)
   - My account, Profile, Logout
   - User-specific links

### 5. Mobile App Support

**Configuration in `aristotle.settings.yml`:**

```yaml
mobile_app_premium_logo: 0  # Can be enabled for branded mobile app
```

**Aristotle + Opigno Mobile Integration:**
- Responsive design adapts to mobile app webview
- API-friendly content rendering
- Offline-compatible layouts
- Push notification ready

### 6. Theming Hooks

**Opigno modules provide Aristotle with:**

- Template suggestions for LMS content
- CSS classes for learning elements
- JavaScript behaviors for interactions
- Theme preprocessors for data formatting

---

## Theme Customization for Opigno

### Recommended Customization Approach

When customizing Aristotle for Opigno:

1. **Create a Sub-theme:**
   ```bash
   mkdir web/themes/custom/my_learning_theme
   ```

2. **Inherit from Aristotle:**
   ```yaml
   # my_learning_theme.info.yml
   name: My Learning Theme
   type: theme
   base theme: aristotle
   core_version_requirement: ^9 || ^10

   regions:
     admin_opigno: 'Opigno Admin'
     # ... inherit other Aristotle regions
   ```

3. **Override Opigno Templates:**
   ```
   web/themes/custom/my_learning_theme/
   └── templates/
       ├── opigno/
       │   ├── opigno-dashboard.html.twig
       │   ├── learning-path-progress.html.twig
       │   └── opigno-calendar-block.html.twig
       └── views/
           └── views-view--opigno-calendar.html.twig
   ```

4. **Custom CSS for Opigno Elements:**
   ```css
   /* Opigno-specific styling */
   .opigno-dashboard-widget { }
   .learning-path-steps { }
   .opigno-calendar-event { }
   .course-catalog-item { }
   ```

### Regions to Preserve

**Critical for Opigno functionality:**
- `admin_opigno` - Admin menu region
- `sidebar_first` - Course navigation
- `content` - Dashboard widgets
- `menu` - Main navigation

### CSS Classes Used by Opigno

**Common Opigno CSS classes in Aristotle:**

```css
/* Dashboard */
.opigno-dashboard
.opigno-dashboard-widget
.dashboard-widget-container

/* Learning Paths */
.learning-path-list
.learning-path-item
.learning-path-progress
.lp-steps-block

/* Calendar */
.opigno-calendar
.calendar-event
.calendar-month-view

/* Training Catalog */
.training-catalog
.training-catalog-item
.catalog-filter

/* Notifications */
.opigno-notification
.notification-unread
.notification-list
```

---

## Configuration Files Reference

### Install Configuration (Required)

1. **`system.theme.yml`** - Theme activation
2. **`aristotle.settings.yml`** - Theme settings and branding
3. **`opigno_dashboard.settings.yml`** - Dashboard widget configuration
4. **`block.block.opigno_admin.yml`** - Opigno admin menu block
5. **`block.block.opigno_training_catalog_filter.yml`** - Catalog filter block
6. **`system.menu.opigno-admin.yml`** - Opigno admin menu definition

### Optional Configuration (Feature-Specific)

1. **`block.block.lp_steps_block.yml`** - Learning path navigation
2. **`block.block.views_block__opigno_calendar_month_block.yml`** - Calendar block
3. **`block.block.dashboard_views_block_opigno_notifications_block_unread_dashboard.yml`** - Notifications
4. **`block.block.dashboard_views_block_opigno_group_members_block_pending.yml`** - Group management
5. **`block.block.dashboard_views_block_opigno_score_modules_dashboard_notavaluated_modules.yml`** - Grading queue
6. **`block.block.dashboard_views_block_opigno_calendar_month_block.yml`** - Dashboard calendar widget

---

## Best Practices

### Theme Development

1. **Always use a sub-theme** - Never modify Aristotle directly
2. **Preserve Opigno regions** - Don't remove `admin_opigno` or other LMS regions
3. **Test dashboard layouts** - Verify widget rendering in all configurations
4. **Maintain responsive design** - Mobile learners are primary users
5. **Follow Opigno CSS conventions** - Use existing classes when possible

### Block Management

1. **Respect visibility rules** - Learning path blocks need correct path visibility
2. **Weight matters** - Block ordering affects user experience
3. **Dashboard performance** - Limit enabled widgets to improve load times
4. **Cache considerations** - Opigno blocks may have user-specific content

### Accessibility

1. **Keyboard navigation** - All Opigno menus must be keyboard accessible
2. **Screen reader support** - Dashboard widgets need proper ARIA labels
3. **Color contrast** - Maintain WCAG AA standards for learning content
4. **Focus indicators** - Visible focus states for all interactive elements

---

## Troubleshooting

### Dashboard Not Displaying

**Symptoms:** Blank dashboard or missing widgets

**Solutions:**
1. Verify `opigno_dashboard.settings.yml` theme setting
2. Check block permissions for current user role
3. Clear Drupal cache: `drush cache:rebuild`
4. Verify widget availability in dashboard settings

### Opigno Admin Menu Missing

**Symptoms:** Admin menu not visible

**Solutions:**
1. Check user has administrator role
2. Verify `admin_opigno` region exists in theme
3. Confirm block is enabled and placed in correct region
4. Clear cache and check block visibility settings

### Learning Path Steps Not Showing

**Symptoms:** LP navigation missing on module pages

**Solutions:**
1. Verify URL matches visibility path pattern
2. Check `lp_steps_block` is enabled
3. Confirm user has access to view learning path
4. Verify `sidebar_first` region is rendered on current page

### Theme Conflicts

**Symptoms:** Styling broken after theme change

**Solutions:**
1. Ensure new theme is Aristotle-based or compatible
2. Export and reimport block configurations
3. Rebuild theme registry: `drush cache:rebuild`
4. Check for CSS conflicts in browser dev tools

---

## Additional Resources

**Official Documentation:**
- Aristotle Theme: https://www.drupal.org/project/aristotle
- Opigno Documentation: https://opigno.org/documentation
- Drupal Theming Guide: https://www.drupal.org/docs/theming-drupal

**Related Cloud3src Documentation:**
- [THEME.md](THEME.md) - Aristotle theme customization
- [FEATURES.md](FEATURES.md) - Complete Opigno feature reference
- [CONFIGURATION.md](CONFIGURATION.md) - Configuration guide

---

**Document Version:** 1.0
**Last Updated:** 2025-11-10
**Distribution:** Cloud3src 1.0.1
**Theme:** Aristotle ~3.2.0
**Opigno:** 3.2.0
