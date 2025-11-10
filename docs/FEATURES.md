# Features Guide - Cloud3src LMS

This comprehensive guide covers all learning management features included in the Cloud3src distribution.

## Table of Contents

- [Learning Management](#learning-management)
- [Content Creation](#content-creation)
- [User Management](#user-management)
- [Assessment & Grading](#assessment--grading)
- [Collaboration Features](#collaboration-features)
- [Reporting & Analytics](#reporting--analytics)
- [Integration Features](#integration-features)
- [Administrative Features](#administrative-features)

## Learning Management

### Learning Paths (Opigno Learning Paths)

**Purpose:** Create structured, sequential learning journeys for learners.

**Key Capabilities:**

- **Structured Curriculum:** Organize courses in logical sequence
- **Prerequisites:** Enforce completion order
- **Mandatory/Optional:** Mix required and elective content
- **Progress Tracking:** Monitor learner advancement
- **Completion Certificates:** Award upon finishing

**Access:** **Administration → Learning paths**

**Creating a Learning Path:**

1. Navigate to **Learning paths → Add learning path**
2. Configure:
   - Title and description
   - Duration estimate
   - Skills covered
   - Prerequisite requirements
3. Add modules (courses) to the path
4. Set module order and prerequisites
5. Configure completion criteria
6. Publish to make available

**Best Practices:**
- Start with clear learning objectives
- Logical progression from basic to advanced
- Mix content types (theory, practice, assessment)
- Provide estimated completion times
- Regular checkpoints and assessments

### Courses & Modules (Opigno Modules)

**Purpose:** Individual learning units containing lessons and activities.

**Module Types:**

1. **Course Modules:** Structured learning content
2. **Meeting Modules:** Virtual classroom sessions
3. **ILT (Instructor-Led Training):** Physical classroom events
4. **H5P Modules:** Interactive content packages
5. **SCORM Modules:** Import SCORM packages

**Creating a Course Module:**

1. Navigate to **Content → Add content → Module**
2. Configure module settings:
   - Title and description
   - Estimated duration
   - Skills taught
   - Grading method
3. Add activities (see Activities section below)
4. Set activity sequence
5. Configure module options
6. Publish

**Module Options:**
- Allow reattempt
- Randomize activities
- Backwards navigation
- Mandatory activities
- Time restrictions
- Prerequisites

### Activities

**Activity Types Available:**

#### 1. **Slides (Presentations)**
- PDF presentations
- PowerPoint slides converted to images
- Online slide viewers
- Embedded presentations

#### 2. **Video Content**
- Embedded YouTube/Vimeo videos
- Self-hosted video files
- Video progress tracking
- Interactive video elements

#### 3. **Documents**
- PDF documents
- Word documents
- Downloadable resources
- Required reading materials

#### 4. **H5P Interactive Content**
- Interactive video
- Course presentations
- Interactive quizzes
- Drag-and-drop exercises
- Timeline visualizations
- Memory games
- And 50+ other H5P content types

#### 5. **External Packages**
- SCORM 1.2 packages
- SCORM 2004 packages
- Tin Can API/xAPI packages

#### 6. **Assessments**
- Quizzes
- Tests
- Exams
- Practice exercises

**Managing Activities:**

Navigate to: **Module edit page → Activities tab**

- Add activities
- Reorder with drag-and-drop
- Set mandatory/optional
- Configure activity-specific settings

### H5P Interactive Content

**Included H5P Library Version:** 5.4 MB comprehensive library

**Popular H5P Content Types:**

1. **Course Presentation:** PowerPoint-like presentations with interactivity
2. **Interactive Video:** Videos with embedded questions and navigation
3. **Question Set:** Collections of various question types
4. **Branching Scenario:** Choose-your-own-adventure style learning
5. **Timeline:** Historical or process timelines
6. **Memory Game:** Educational matching games
7. **Drag and Drop:** Visual categorization exercises
8. **Fill in the Blanks:** Text completion exercises
9. **Accordion:** Collapsible content sections
10. **Flashcards:** Digital study cards

**Creating H5P Content:**

1. Navigate to: **Content → Add content → Interactive Content**
2. Choose content type from library
3. Configure content:
   - Add text, images, videos
   - Set interaction points
   - Configure behavior settings
4. Preview and test
5. Save and embed in modules

**H5P Integration Benefits:**
- No Flash required (HTML5)
- Mobile-friendly
- Results tracked in Opigno
- Reusable content
- Export/import capability

## Content Creation

### Media Library

**Media Types Supported:**

1. **Images:**
   - JPG, PNG, GIF formats
   - Image styles automatically applied
   - Alt text for accessibility
   - Used in courses, pages, H5P

2. **Videos:**
   - Self-hosted video files
   - Embedded YouTube/Vimeo
   - Automatic thumbnail generation
   - Progress tracking when used in modules

3. **Audio:**
   - MP3, WAV formats
   - Audio player embedded
   - Used in H5P content
   - Podcast-style content

4. **Files:**
   - PDF, DOC, DOCX, XLS, XLSX
   - ZIP archives
   - Any file type for download
   - Public or private access

**Managing Media:**

Navigate to: **Content → Media**

- Upload files
- Organize with folders (Media Library module)
- Edit metadata
- Reuse across content
- Bulk upload capabilities

### Text Formats & Editors

**Available Text Formats:**

1. **Full HTML:**
   - Complete HTML editing
   - All tags allowed
   - CKEditor with full toolbar
   - For trusted users only

2. **Basic HTML:**
   - Limited safe HTML tags
   - Standard formatting options
   - Suitable for most content creators

3. **Restricted HTML:**
   - Minimal HTML tags
   - Plain text with limited formatting
   - For user comments

**CKEditor Features:**

- WYSIWYG editing
- Image upload and embed
- Media browser integration
- Background images (CKEditor Background Image module)
- Table creation
- Source code editing
- Font selection
- Special characters
- Link management

### Pages & Content Types

**Content Type: Page**

Use for static content pages:
- About pages
- Help documentation
- Policy pages
- General information

**Creating a Page:**

Navigate to: **Content → Add content → Page**

1. Enter title
2. Add body content with CKEditor
3. Configure display settings
4. Set URL alias
5. Configure menu placement
6. Publish

## User Management

### User Roles

**Pre-configured Roles:**

1. **Administrator:**
   - Full system access
   - All permissions
   - Site configuration
   - User management

2. **Student Manager:**
   - Create and manage student accounts
   - Enroll users in training
   - View student progress
   - Limited administrative access

3. **Content Manager:**
   - Create and edit courses
   - Manage learning content
   - Configure modules
   - Cannot manage users

4. **User Manager:**
   - User account management
   - Role assignment
   - User delegation
   - No content access

**Managing Roles:**

Navigate to: **Administration → People → Roles**

### Groups (Drupal Group Module)

**Purpose:** Organize learners into cohorts, departments, or teams.

**Group Features:**

- **Group Content:** Assign courses to specific groups
- **Group Roles:** Define roles within groups
- **Group Permissions:** Control access per group
- **Group Membership:** Manual or automatic enrollment
- **Flexible Membership:** Multiple groups per user

**Creating a Group:**

1. Navigate to: **Groups → Add group**
2. Configure:
   - Group name
   - Description
   - Group type
   - Visibility (public/private)
3. Add members
4. Assign content to group
5. Configure group roles and permissions

**Use Cases:**
- Department-specific training
- Cohort-based learning
- Team collaboration spaces
- Role-based content access

### User Profiles

**Profile Features:**

- User picture/avatar
- Bio/description
- Skills and interests
- Learning progress
- Certificates earned
- Activity history

**Profile Configuration:**

Navigate to: **Configuration → People → Account settings**

- Add custom fields
- Configure display
- Set required fields
- Control privacy settings

### Private Messaging

**Purpose:** Internal communication between users.

**Features:**

- One-on-one messaging
- Message threads
- Message notifications
- Attachments support
- Read/unread status

**Access:** User menu → Messages

**Best Practices:**
- Enable email notifications
- Set up moderation for safety
- Configure retention policies
- Monitor for inappropriate use

## Assessment & Grading

### Quiz & Test Creation

**Quiz Features:**

- **Multiple Question Types:**
  - Multiple choice
  - True/False
  - Fill in the blank
  - Long answer
  - Matching
  - Scale (Likert)

- **Quiz Configuration:**
  - Time limits
  - Number of attempts
  - Question randomization
  - Feedback settings
  - Pass/fail threshold
  - Certificate on pass

**Creating a Quiz:**

1. Navigate to: **Content → Add content → Quiz**
2. Configure quiz settings
3. Add questions
4. Set scoring rules
5. Configure result feedback
6. Add to module

### Grading System

**Grading Methods:**

1. **Automatic Grading:**
   - Quiz scores calculated automatically
   - H5P content auto-graded
   - Immediate feedback

2. **Manual Grading:**
   - Essay questions
   - Assignment submissions
   - Instructor review required

3. **Mixed Grading:**
   - Combination of auto and manual
   - Partial automation

**Grade Management:**

Navigate to: **Module → Results tab**

- View all learner attempts
- Override automatic grades if needed
- Provide written feedback
- Export grade data

### Certificates

**Purpose:** Award completion certificates to learners.

**Certificate Features:**

- Customizable templates
- Dynamic data (name, date, course)
- PDF generation
- Automatic awarding on completion
- Certificate expiration dates
- Download and print

**Configuring Certificates:**

1. Navigate to: **Configuration → Opigno → Certificates**
2. Create certificate template
3. Design layout with HTML/CSS
4. Add dynamic tokens (user name, course title, date)
5. Assign to learning paths/modules
6. Set completion criteria

## Collaboration Features

### Calendar

**Two Calendar Systems:**

1. **Opigno Calendar:**
   - Learning-specific events
   - Course deadlines
   - ILT sessions
   - Meeting schedules

2. **Drupal Calendar:**
   - General events
   - Announcements
   - System maintenance

**Calendar Features:**

- Month/week/day views
- Event creation
- Recurring events
- Reminders and notifications
- ICS export
- iCal integration

**Access:** Main menu → Calendar

### Forum

**Purpose:** Discussion boards for learners.

**Forum Features:**

- Topic creation
- Threaded discussions
- File attachments
- User subscriptions
- Moderation tools
- Search functionality

**Forum Structure:**

- Multiple forums
- Forum categories
- Topic status (open/closed)
- Pinned topics
- User reputation/badges

**Creating Forums:**

Navigate to: **Structure → Forums**

### Social Features

**User Connections:**
- Follow other users
- Friend requests
- Connection lists
- Activity feeds

**Activity Stream:**
- Recent actions
- New content notifications
- Course completions
- Certificate awards

**Badges & Gamification:**
- Achievement badges
- Point systems
- Leaderboards
- Progress visualizations

## Reporting & Analytics

### Statistics Module (Opigno Statistics)

**Purpose:** Track and analyze learner performance and engagement.

**Available Reports:**

1. **User Statistics:**
   - Individual learner progress
   - Time spent in courses
   - Test scores
   - Completion rates
   - Learning path status

2. **Course Statistics:**
   - Enrollment numbers
   - Completion rates
   - Average scores
   - Popular courses
   - Drop-off points

3. **Group Statistics:**
   - Group performance
   - Comparative analysis
   - Group progress
   - Aggregate scores

4. **System Statistics:**
   - Platform usage
   - Active users
   - Content consumption
   - Peak usage times

**Access:** Main menu → Statistics

**Generating Reports:**

1. Navigate to desired report type
2. Select date range
3. Choose filters (users, courses, groups)
4. Generate report
5. Export to CSV/PDF if needed

### Dashboard Widgets

**Purpose:** Personalized learning dashboard for users.

**Available Widgets:**

- **My Progress:** Current learning path status
- **Recent Activity:** Latest actions and updates
- **Upcoming Events:** Calendar integration
- **My Achievements:** Certificates and badges
- **Recommended Courses:** Personalized suggestions
- **My Groups:** Group memberships
- **Messages:** Unread message count
- **Latest Forum Posts:** Community updates

**Configuring Dashboard:**

Navigate to: **Configuration → Opigno → Dashboard settings**

- Enable/disable widgets
- Set default layout
- Configure widget settings
- Allow user customization

### xAPI / Tin Can API

**Purpose:** Track detailed learning analytics and send to Learning Record Store (LRS).

**Features:**

- Statement tracking
- Learning analytics
- LRS integration
- Detailed activity logs
- Cross-platform tracking

**Configuration:**

Navigate to: **Configuration → Opigno → Tin Can settings**

1. Enter LRS endpoint URL
2. Configure authentication
3. Map activities to xAPI verbs
4. Test connection
5. Enable tracking

**Tracked Actions:**
- Course started/completed
- Video watched
- Quiz attempted/passed
- Document viewed
- H5P interactions

## Integration Features

### SCORM Support

**Purpose:** Import and use SCORM-compliant e-learning packages.

**Supported Versions:**
- SCORM 1.2
- SCORM 2004 (3rd & 4th edition)

**Importing SCORM:**

1. Navigate to: **Content → Add content → SCORM Package**
2. Upload .zip SCORM package
3. Configure display options
4. Add to module
5. Test playback

**SCORM Features:**
- Progress tracking
- Score reporting
- Bookmark/resume
- Full-screen mode

### Mobile App Support

**Opigno Mobile App Compatibility:**

The distribution is compatible with the Opigno mobile app:

- iOS and Android apps available
- Offline course access
- Progress synchronization
- Push notifications
- Mobile-optimized content

**Configuration:**

Navigate to: **Configuration → Opigno → Mobile app settings**

### Email Integration

**Email Features:**

- **Mail System Module:** Advanced email handling
- **Mime Mail Module:** HTML email support
- **Queue Mail Module:** Batch email sending

**Email Types:**
- User registration
- Course enrollment
- Certificate awards
- Message notifications
- Assignment reminders
- Forum subscriptions

**Configuration:**

Navigate to: **Configuration → System → Mail System**

### Commerce Integration

**Purpose:** Sell courses and learning paths.

**Commerce Features:**
- Product catalog
- Payment gateway integration
- Order management
- Discount codes
- Purchase history

**Note:** Basic commerce framework included; additional configuration required for full e-commerce.

## Administrative Features

### Configuration Management

**Purpose:** Export/import site configuration.

**Configuration Sync:**

All 134 configuration files can be:
- Exported to YAML
- Version controlled
- Deployed across environments
- Imported to other sites

**Using Configuration Management:**

```bash
# Export configuration
drush config:export

# Import configuration
drush config:import

# View configuration changes
drush config:status
```

### Update Management

**Keeping Cloud3src Updated:**

```bash
# Update Drupal core and modules
composer update drupal/core --with-dependencies
composer update

# Run database updates
drush updatedb

# Clear cache
drush cache:rebuild

# Export new configuration
drush config:export
```

### Backup & Recovery

**Recommended Backup Strategy:**

1. **Database:** Daily automated backups
2. **Files:** Backup public and private files
3. **Configuration:** Version control config directory
4. **Code:** Version control custom code

**Backup Command:**
```bash
drush sql:dump --gzip --result-file=backup.sql.gz
tar -czf files-backup.tar.gz web/sites/default/files
```

### Performance Optimization

**Performance Settings:**

Navigate to: **Configuration → Development → Performance**

1. **Cache Settings:**
   - Page cache for anonymous users
   - Block cache
   - CSS aggregation and compression
   - JavaScript aggregation and compression

2. **Bandwidth Optimization:**
   - Enable CSS aggregation
   - Enable JS aggregation
   - Image style optimization

3. **External Cache:**
   - Redis (recommended)
   - Memcache
   - Varnish for high traffic

### Security Features

**Built-in Security:**

- User protection module
- Private file system
- Role-based access control
- Two-factor authentication support
- Security review module (install separately)

**Security Best Practices:**

1. Regular updates
2. Strong password policies
3. HTTPS enforcement
4. File upload restrictions
5. Regular security audits

## Module Reference

### Core Opigno Modules (40+)

1. **opigno_lms** - Core LMS functionality
2. **opigno_learning_path** - Learning path management
3. **opigno_module** - Course modules
4. **opigno_calendar** - Event scheduling
5. **opigno_catalog** - Course catalog
6. **opigno_certificate** - Certificate generation
7. **opigno_dashboard** - User dashboard
8. **opigno_forum** - Discussion forums
9. **opigno_messaging** - Private messaging
10. **opigno_statistics** - Analytics and reporting
11. **opigno_skills** - Skills tracking
12. **opigno_social** - Social features
13. **opigno_tincan_api** - xAPI/LRS integration
14. **opigno_scorm** - SCORM support
15. **opigno_h5p** - H5P integration

...and 25+ additional Opigno modules for specific features.

### Key Contributed Modules

- **group** - User organization
- **h5p** - Interactive content
- **entity_browser** - Media selection
- **entity_embed** - Content embedding
- **commerce** - E-commerce framework
- **search_api** - Advanced search
- **token** - Dynamic text replacement
- **field_group** - Form organization
- **entity_print** - PDF generation

## Next Steps

- **[Installation Guide](INSTALLATION.md)** - Set up your LMS
- **[Theme Customization](THEME.md)** - Brand your platform
- **[Configuration Guide](CONFIGURATION.md)** - Customize settings

---

**Version:** 1.0.1 | **Based on:** Opigno 3.2.0 | **Last Updated:** 2025-11-10
