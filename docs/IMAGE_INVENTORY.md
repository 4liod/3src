# Image Inventory - Cloud3src Theme

This document provides a complete inventory of all images and image-related assets in the Cloud3src Drupal LMS distribution.

**Generated:** 2025-11-10
**Distribution Version:** 1.0.1

---

## Table of Contents

- [Images Included in Repository](#images-included-in-repository)
- [Theme Images (Aristotle)](#theme-images-aristotle)
- [Image Styles Configuration](#image-styles-configuration)
- [User Picture Configuration](#user-picture-configuration)
- [Media Type Configuration](#media-type-configuration)
- [Image Requirements Summary](#image-requirements-summary)

---

## Images Included in Repository

### 1. Login Background Image

**File:** `images/3src_Image_connexion_1600-829_2.jpg`

**Specifications:**
- **Format:** JPEG (Progressive)
- **Dimensions:** 1600 × 825 pixels
- **Aspect Ratio:** 1.94:1 (approximately 16:9)
- **File Size:** 890 KB
- **Original Dimensions:** 3456 × 5184 pixels (resized)
- **Color Space:** RGB
- **Compression:** Progressive JPEG, 8-bit precision
- **Orientation:** Horizontal/Landscape

**Purpose:**
- Login page background image
- Homepage slideshow slide (optional)
- Hero banner for anonymous users

**Visual Description:**
The image shows a close-up, artistic macro photograph with a shallow depth of field. It features cool blue tones (cyan and slate) with a soft, blurred bokeh effect in the background. The foreground appears to show fine details of an object (possibly fabric or natural texture) with water droplets or crystalline structures. The overall mood is calm, professional, and modern.

**Usage in Configuration:**
- Referenced in `config/install/aristotle.settings.yml` as `4LIOD-login-image.jpg`
- Copied to public files during installation via `cloud3src.install:69-70`
- Used as homepage slideshow background

**Recommended Use Cases:**
- Login page background
- Homepage hero section
- Slideshow background for welcome page
- Email template background (if needed)

**Optimization Notes:**
- File size is 890KB - consider optimization for web delivery
- Recommended optimized size: 300-400KB without visible quality loss
- Already at web-optimized dimensions (1600px width)
- Progressive JPEG format allows faster loading

---

## Theme Images (Aristotle)

These images are **referenced** in the configuration but are **expected to be provided** in the Aristotle theme directory after installation. They are **not included** in this repository.

### Expected Location
`web/themes/contrib/aristotle/assets/`

### 2. Standard Logo (Authenticated Users)

**Expected File:** `themes/aristotle/assets/4LIOD.svg`

**Referenced In:**
- `config/install/aristotle.settings.yml` (line 11)
- `cloud3src.install` (line 49)

**Specifications:**
- **Format:** SVG (Recommended)
- **Alternative Formats:** PNG with transparency
- **Recommended Dimensions:** 200-250px width, auto height
- **Aspect Ratio:** Typically 2:1 to 4:1 (horizontal logo)
- **Color:** Primary brand colors
- **Background:** Transparent

**Purpose:**
- Main site logo displayed in header
- Visible to authenticated (logged-in) users
- Primary brand identifier

**Implementation Notes:**
- SVG format recommended for scalability
- Should work well on light backgrounds
- Must be placed in Aristotle theme assets folder
- Currently referenced as "4LIOD.svg" - replace with your logo

**Customization:**
```bash
# To use your own logo:
cp your-company-logo.svg web/themes/contrib/aristotle/assets/4LIOD.svg

# Or update the configuration to point to your file
# Edit: config/install/aristotle.settings.yml
# Change: path: themes/aristotle/assets/your-logo.svg
```

### 3. Anonymous User Logo (Login Page)

**Expected File:** `themes/aristotle/assets/4LIOD-white.svg`

**Referenced In:**
- `config/install/aristotle.settings.yml` (line 13)
- `cloud3src.install` (line 54)

**Specifications:**
- **Format:** SVG (Recommended)
- **Alternative Formats:** PNG with transparency
- **Recommended Dimensions:** Same as standard logo (200-250px width)
- **Aspect Ratio:** Match standard logo
- **Color:** White or light variant
- **Background:** Transparent

**Purpose:**
- Logo displayed on login page
- Optimized for dark or image backgrounds
- Visible to anonymous (non-authenticated) users
- Used before user authentication

**Implementation Notes:**
- Typically a white or light-colored version of the main logo
- Must contrast with login page background
- Should match dimensions of standard logo
- SVG format allows color flexibility

**Customization:**
```bash
# To use your own white logo:
cp your-company-logo-white.svg web/themes/contrib/aristotle/assets/4LIOD-white.svg
```

### 4. Login Page Background Image

**Expected File:** `themes/aristotle/assets/4LIOD-login-image.jpg`

**Referenced In:**
- `config/install/aristotle.settings.yml` (line 5)
- `cloud3src.install` (line 65)

**Specifications:**
- **Format:** JPG (for photographs) or PNG (for graphics)
- **Recommended Dimensions:** 1920 × 1080px (Full HD)
- **Alternative Dimensions:** 2560 × 1440px (2K) for retina displays
- **Aspect Ratio:** 16:9
- **File Size Target:** 200-500 KB (optimized)
- **Orientation:** Landscape/Horizontal

**Purpose:**
- Background image for login page
- Optional homepage slideshow slide
- Creates branded login experience

**Implementation Notes:**
- Copied from installation profile during setup
- Repository provides default image (`images/3src_Image_connexion_1600-829_2.jpg`)
- Installation process copies it to theme assets
- Can be customized by replacing the file

**Visual Recommendations:**
- Use subtle, non-distracting imagery
- Ensure text readability over image
- Consider dark overlay for better contrast
- Professional, brand-aligned photography
- Avoid busy patterns that compete with login form

**Customization:**
```bash
# Copy the included image to theme:
cp images/3src_Image_connexion_1600-829_2.jpg \
   web/themes/contrib/aristotle/assets/4LIOD-login-image.jpg

# Or use your own custom image:
cp your-custom-background.jpg \
   web/themes/contrib/aristotle/assets/4LIOD-login-image.jpg
```

---

## Image Styles Configuration

Image styles are automated image processing configurations that create derivative images from originals. These are pre-configured in the distribution.

### 5. Catalog Thumbnail

**Configuration File:** `config/optional/image.style.catalog_thumbnail.yml`

**Style Name:** `catalog_thumbnail`
**Label:** "Catalog thumbnail"

**Processing:**
- **Effect:** Scale and Crop
- **Width:** 545 pixels
- **Height:** 340 pixels
- **Aspect Ratio:** 1.6:1 (approximately 16:10)
- **Anchor:** Center-center (default)

**Purpose:**
- Course/training catalog grid display
- Main course listing pages
- Featured course displays
- Browse/search results

**Usage Context:**
- Displayed in training catalog view
- Multiple thumbnails per page
- Clickable links to full course details

**Original Image Recommendations:**
- Upload minimum: 1090 × 680 pixels (2× for retina)
- Recommended: 1635 × 1020 pixels (3× for retina)
- Format: JPG for photos, PNG for graphics
- File size: 200-500 KB before processing

### 6. Learning Path Thumbnail

**Configuration File:** `config/optional/image.style.learning_path_thumbnail.yml`

**Style Name:** `learning_path_thumbnail`
**Label:** "Learning path thumbnail"

**Processing:**
- **Effect:** Scale and Crop
- **Width:** 318 pixels
- **Height:** 318 pixels
- **Aspect Ratio:** 1:1 (Square)
- **Anchor:** Center-center

**Purpose:**
- Learning path cards
- Square profile-style thumbnails
- Compact course path displays
- Dashboard widgets

**Usage Context:**
- Learning path listings
- User dashboard "My Paths" widget
- Related path suggestions
- Mobile-optimized displays

**Original Image Recommendations:**
- Upload minimum: 636 × 636 pixels (2× for retina)
- Recommended: 954 × 954 pixels (3× for retina)
- Format: JPG or PNG
- Composition: Center important elements (square crop)
- File size: 150-300 KB before processing

### 7. Training List Item Image

**Configuration File:** `config/optional/image.style.training_list_item_image.yml`

**Style Name:** `training_list_item_image`
**Label:** "Training list item image (45×40)"

**Processing:**
- **Effect:** Scale and Crop
- **Width:** 45 pixels
- **Height:** 40 pixels
- **Aspect Ratio:** 1.125:1 (9:8)
- **Anchor:** Center-center

**Purpose:**
- Tiny thumbnails for compact lists
- Training list item icons
- Recent activity thumbnails
- Dropdown menu icons

**Usage Context:**
- Compact list views
- Navigation dropdowns
- Activity feeds
- Mobile navigation

**Original Image Recommendations:**
- Upload minimum: 90 × 80 pixels (2× for retina)
- Recommended: Use same source as larger thumbnails
- Format: JPG or PNG
- Note: Very small display - use simple, recognizable imagery
- File size: Any (will be dramatically reduced)

---

## User Picture Configuration

### 8. User Profile Pictures (Avatars)

**Configuration File:** `config/install/field.field.user.user.user_picture.yml`

**Field Name:** `user_picture`
**Label:** "Picture"
**Description:** "Your virtual face or picture."

**Upload Specifications:**
- **Allowed Extensions:** `png gif jpg jpeg`
- **Maximum File Size:** 3 MB
- **Maximum Resolution:** 220 × 220 pixels
- **Minimum Resolution:** None specified
- **Aspect Ratio:** Square recommended (1:1)
- **Required:** No (optional)
- **Storage Path:** `pictures/[date:custom:Y]-[date:custom:m]/`
  - Example: `pictures/2025-11/user-avatar.jpg`

**Features:**
- **Alt Text:** Not required (disabled)
- **Title Field:** Not required (disabled)
- **Translatable:** Yes (multilingual support)
- **Default Image:** None configured

**Purpose:**
- User profile avatars
- Comment author identification
- Forum post attribution
- Messaging system avatars
- Course completion displays

**Display Contexts:**
- User profile page
- Comments on courses/forums
- Private messages
- Dashboard widgets
- Certificate displays (optional)

**Configuration Settings:**
```yaml
features:
  node_user_picture: 0         # Disabled for content authorship
  comment_user_picture: 1      # Enabled for comments/forums
  comment_user_verification: 1 # Show verified status
```

**User Picture Best Practices:**
- Encourage square images (220×220px)
- Accept common formats (JPG, PNG, GIF)
- 3 MB limit accommodates high-quality photos
- Auto-resize to 220×220 if larger
- Recommend professional headshots for learning environment
- Consider default avatar for users without pictures

**Implementation:**
- Users upload via: **My Account → Edit → Picture**
- Admin upload via: **People → Edit user → Picture**
- Storage in public files: `sites/default/files/pictures/YYYY-MM/`

---

## Media Type Configuration

The distribution supports multiple media types with image handling capabilities.

### 9. Image Media Type

**Configuration:** `config/optional/core.entity_form_display.media.image.default.yml`

**Supported Formats:**
- JPEG/JPG
- PNG
- GIF (including animated)
- WebP (if server supports)

**Use Cases:**
- Course content images
- Embedded images in lessons
- Downloadable resources
- Gallery displays
- Featured images for content

**Media Library Features:**
- Drag-and-drop upload
- Bulk upload capability
- Reusable across content
- Metadata management
- Image cropping tools
- Alternative text management
- SEO-friendly naming

**Integration:**
- CKEditor image embedding
- Entity browser selection
- H5P content integration
- WYSIWYG editors

---

## Image Requirements Summary

### Quick Reference Table

| Image Type | Format | Dimensions (px) | File Size | Purpose |
|------------|--------|----------------|-----------|---------|
| **Login Background** | JPG | 1600 × 825 | 890 KB | Login page background |
| **Standard Logo** | SVG/PNG | 200-250 width | <100 KB | Header logo (authenticated) |
| **Anonymous Logo** | SVG/PNG | 200-250 width | <100 KB | Login page logo |
| **Catalog Thumbnail** | JPG/PNG | 545 × 340 | Auto | Course catalog |
| **Learning Path Thumb** | JPG/PNG | 318 × 318 | Auto | Learning path cards |
| **List Item Image** | JPG/PNG | 45 × 40 | Auto | Compact lists |
| **User Picture** | JPG/PNG/GIF | 220 × 220 max | 3 MB max | User avatars |
| **Homepage Slideshow** | JPG/PNG | 1920 × 1080 | 200-500 KB | Hero banners |
| **Header Background** | JPG/PNG | 1920 × 400 | 100-200 KB | Optional header |

### Recommended Upload Dimensions

For best quality across all devices (including retina displays), upload images at these source dimensions:

| Use Case | Source Dimensions | Notes |
|----------|-------------------|-------|
| Catalog Images | 1635 × 1020 | 3× retina quality |
| Learning Path | 954 × 954 | 3× retina quality |
| Course Headers | 1920 × 1080 | Full HD standard |
| User Avatars | 440 × 440 | 2× retina quality |
| Logos | SVG (vector) | Infinite scalability |
| Slideshow | 2560 × 1440 | 2K for retina displays |

---

## Image Optimization Recommendations

### Compression Guidelines

**Photography (JPG):**
- Quality: 85% (good balance)
- Progressive encoding: Yes
- Chroma subsampling: 4:2:0
- Strip metadata: Yes (except copyright)
- Target compression: 60-70% size reduction

**Graphics (PNG):**
- Color depth: 24-bit (or 8-bit if <256 colors)
- Compression level: Maximum (lossless)
- Interlacing: Yes (for progressive loading)
- Remove unused colors: Yes

**Logos (SVG):**
- Optimize paths: Yes
- Remove editor metadata: Yes
- Minify: Yes
- Target: <50 KB for complex logos

### Tools for Optimization

**Online Tools:**
- TinyPNG/TinyJPG (PNG/JPG compression)
- SVGOMG (SVG optimization)
- Squoosh (Google's image optimizer)

**Command Line Tools:**
```bash
# Optimize JPEG
jpegoptim --max=85 --strip-all image.jpg

# Optimize PNG
optipng -o7 image.png

# Optimize SVG
svgo logo.svg

# Batch optimize
find images/ -name "*.jpg" -exec jpegoptim --max=85 --strip-all {} \;
```

**Drupal Modules:**
- ImageAPI Optimize (automatic optimization)
- ImageMagick (better quality than GD)
- WebP module (modern format support)

---

## Image Asset Checklist

Use this checklist when preparing images for Cloud3src:

### Pre-Installation Checklist

- [ ] Create or acquire standard logo (SVG preferred)
- [ ] Create white/light variant of logo for dark backgrounds
- [ ] Select or create login background image (1920×1080)
- [ ] Optimize all images for web delivery
- [ ] Verify image licenses/rights
- [ ] Prepare multiple homepage slideshow images (optional)
- [ ] Create default user avatar (optional)

### Post-Installation Checklist

- [ ] Upload logos to `web/themes/contrib/aristotle/assets/`
- [ ] Copy login background to theme assets
- [ ] Configure theme logo settings
- [ ] Test logo display on all pages
- [ ] Upload default user avatar (if using)
- [ ] Create sample course thumbnails
- [ ] Test image styles rendering
- [ ] Verify retina display quality
- [ ] Check mobile responsive images
- [ ] Enable image optimization modules

### Content Creation Checklist

- [ ] Prepare course thumbnail images (545×340 source)
- [ ] Create learning path images (square format)
- [ ] Optimize images before upload
- [ ] Add descriptive alt text
- [ ] Use consistent image styling
- [ ] Test image loading performance
- [ ] Verify accessibility compliance

---

## File Structure

### Current Repository Structure
```
/home/user/3src/
├── images/
│   ├── 3src_Image_connexion_1600-829_2.jpg  (890 KB)
│   └── README.md
├── config/
│   ├── install/
│   │   ├── aristotle.settings.yml           (logo/image references)
│   │   ├── field.field.user.user.user_picture.yml
│   │   └── field.storage.user.user_picture.yml
│   └── optional/
│       ├── image.style.catalog_thumbnail.yml
│       ├── image.style.learning_path_thumbnail.yml
│       └── image.style.training_list_item_image.yml
└── cloud3src.install                        (image copy scripts)
```

### Expected Post-Installation Structure
```
web/
├── themes/contrib/aristotle/assets/
│   ├── 4LIOD.svg                   (your standard logo)
│   ├── 4LIOD-white.svg             (your white logo)
│   └── 4LIOD-login-image.jpg       (login background)
├── sites/default/files/
│   ├── 3src_Image_connexion_1600-829_2.jpg  (copied during install)
│   ├── 4LIOD-login-image.jpg                 (copied during install)
│   ├── pictures/                             (user avatars)
│   │   ├── 2025-11/
│   │   ├── 2025-12/
│   │   └── ...
│   └── styles/                               (generated derivatives)
│       ├── catalog_thumbnail/
│       ├── learning_path_thumbnail/
│       └── training_list_item_image/
└── modules/contrib/
    └── [various modules with image handling]
```

---

## Technical Notes

### Image Processing Pipeline

1. **Upload:** Original image uploaded to media library or field
2. **Validation:** Check file type, size, dimensions
3. **Storage:** Save to public or private files directory
4. **Processing:** Generate image style derivatives on demand
5. **Caching:** Cache generated images for performance
6. **Delivery:** Serve optimized images to browsers

### Image Style Generation

Images are processed on first request:
- Original stored in `files/` directory
- Derivative created in `files/styles/[style_name]/`
- Subsequent requests serve cached derivative
- Derivatives regenerated if style configuration changes

### Performance Considerations

**Optimization:**
- Enable image aggregation
- Use CDN for static assets
- Enable browser caching
- Implement lazy loading
- Use WebP format where supported
- Optimize source images before upload

**Storage:**
- Public files: Publicly accessible images
- Private files: Secure course materials
- Image styles: Auto-generated, can be purged
- Temporary files: Cleaned up automatically

### Accessibility

**Required Practices:**
- Always provide alt text for meaningful images
- Use empty alt="" for decorative images
- Ensure sufficient color contrast
- Provide text alternatives for image content
- Test with screen readers
- Use semantic HTML for image context

---

## References

**Configuration Files:**
- `config/install/aristotle.settings.yml` - Theme image settings
- `config/optional/image.style.*.yml` - Image style definitions
- `config/install/field.field.user.user.user_picture.yml` - User avatar config
- `cloud3src.install` - Installation image setup

**Documentation:**
- [THEME.md](THEME.md) - Aristotle theme customization
- [INSTALLATION.md](INSTALLATION.md) - Installation guide
- [CONFIGURATION.md](CONFIGURATION.md) - Configuration reference

**External Resources:**
- Drupal Image Styles: https://www.drupal.org/docs/user_guide/en/structure-image-styles.html
- Aristotle Theme: https://www.drupal.org/project/aristotle
- Image Optimization: https://www.drupal.org/docs/8/mobile-guide/responsive-images

---

**Document Version:** 1.0
**Last Updated:** 2025-11-10
**Distribution Version:** Cloud3src 1.0.1
