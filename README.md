# Granite - Dual Image Hero Component

## Overview

**Granite** is a sophisticated dual-image hero component with integrated metrics, designed for conference websites, community platforms, and event landing pages. Featuring overlapping imagery with a bold central badge, this component creates visual impact while clearly communicating key metrics and value propositions.

<img width="1606" height="876" alt="_C__Users_STUDENT_Desktop_Projects_Granite_index html" src="https://github.com/user-attachments/assets/e57548a1-80a5-4130-b664-494e64f0821b" />

## Live Demo

[View Live Demo](https://thisislefa.github.io/Granite/)

## Technical Architecture

### Core Stack
- **Tailwind CSS** - Utility-first framework for rapid development
- **Inter Font** - Modern, geometric typeface for clarity
- **Pure HTML/CSS** - No JavaScript dependencies required
- **Responsive Grid** - 10-column layout system with adaptive breakpoints
- **Custom CSS Layer** - Component-specific styles with namespace isolation

### Component Structure

```
Granite Component/
├── Grid Container (10-column responsive)
│   ├── Image Cluster (5 columns)
│   │   ├── Left Image (50% width)
│   │   ├── Right Image (50% width)
│   │   └── Badge Overlay (centered)
│   └── Text Content (5 columns)
│       ├── Pre-header (uppercase tag)
│       ├── Main Headline (H1)
│       ├── Body Paragraphs (x2)
│       └── Call-to-action Button
```

## Design Specifications

### Layout Grid
- **Base:** 10-column layout with responsive collapse
- **Image Cluster:** 5 columns (lg:col-span-5)
- **Text Content:** 5 columns (lg:col-span-5)
- **Mobile:** Single column stacking (grid-cols-1)

### Typography System
- **Font Family:** Inter (400-800 weights)
- **Pre-header:** 0.875rem uppercase with letter-spacing
- **Main Headline:** 3-5rem bold with negative letter-spacing
- **Body Text:** 1-1.125rem with 600 color contrast
- **Badge Text:** 2.25-4rem bold with supporting label

### Color Palette
```css
Primary: #000000 (text, badge, button)
Secondary: #9b9b9b (pre-header)
Background: #f8fafc (light gray)
Accent: #ffffff (badge border, text contrast)
```

### Image Specifications
- **Left Image:** 350-450px height (taller)
- **Right Image:** 300-380px height (shorter)
- **Aspect Ratio:** Free-form with object-fit: cover
- **Border Radius:** 1rem (rounded-2xl)
- **Shadow:** Medium elevation (shadow-lg)

### Badge Design
- **Position:** Absolute center overlay
- **Dimensions:** 32-36rem diameter
- **Background:** Solid black (#000)
- **Border:** 4px white with shadow
- **Content:** Primary metric + label

## Integration Guide

### Basic Implementation

1. **Include Dependencies:**
```html
<!-- Tailwind CSS via CDN -->
<script src="https://cdn.tailwindcss.com"></script>

<!-- Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">

<!-- Component Styles -->
<link rel="stylesheet" href="granite.css">
```

2. **HTML Template:**
```html
<div class="granite-component">
    <div class="grid-container">
        <div class="image-cluster">
            <img src="left-image.jpg" class="left-image" alt="Description">
            <img src="right-image.jpg" class="right-image" alt="Description">
            <div class="badge">
                <span class="metric">30+</span>
                <span class="label">Villages</span>
            </div>
        </div>
        <div class="text-content">
            <p class="pre-header">YOUR TAGLINE</p>
            <h1>Your Main Headline</h1>
            <p>Your body text paragraph one.</p>
            <p>Your body text paragraph two.</p>
            <a href="#" class="action-button">Call to Action</a>
        </div>
    </div>
</div>
```

## Customization Options

### Theming via CSS Variables
```css
:root {
    --granite-primary: #000000;
    --granite-secondary: #9b9b9b;
    --granite-background: #f8fafc;
    --granite-accent: #ffffff;
    --granite-badge-bg: #000000;
    --granite-badge-border: #ffffff;
}
```

### Layout Variants
```html
<!-- Reverse layout (text left, images right) -->
<div class="granite-component reversed">
    <!-- Reversed column order -->
</div>

<!-- Vertical stacking -->
<div class="granite-component stacked">
    <!-- Single column layout -->
</div>

<!-- Full-width variant -->
<div class="granite-component full-width">
    <!-- Expanded grid container -->
</div>
```

### Content Variations
- **Badge Content:** Years, attendees, countries, satisfaction rate
- **Image Ratio:** 60/40 split, vertical stacking, single hero image
- **Button Style:** Outline, gradient, text-only with arrow
- **Header Hierarchy:** H2 subheading, testimonial quote, client logos

## Performance Optimization

### Image Loading Strategy
```html
<!-- Lazy loading with placeholder -->
<img src="image.jpg" 
     loading="lazy"
     decoding="async"
     width="800"
     height="600"
     alt="Description"
     class="granite-image"
     onerror="this.src='fallback.jpg'">
```

### Font Optimization
```css
/* Font loading strategy */
@font-face {
    font-family: 'Inter';
    font-style: normal;
    font-weight: 400;
    font-display: swap;
    src: url('/fonts/inter.woff2') format('woff2');
}
```

### Tailwind Purge Configuration
```javascript
// tailwind.config.js
module.exports = {
    purge: {
        content: ['./**/*.html'],
        safelist: [
            'granite-', // Preserve all granite component classes
            'dc-',      // Preserve component prefix
        ],
    },
}
```

## Accessibility Features

### Semantic Markup
```html
<section class="granite-component" role="region" aria-labelledby="granite-heading">
    <div class="grid-container">
        <div class="image-cluster" aria-label="Community event images">
            <img src="image.jpg" alt="People collaborating at tech conference">
            <img src="image2.jpg" alt="Server room hardware close-up">
            <div class="badge" role="status" aria-label="30 plus villages">
                <span class="sr-only">Over 30</span>
                <span class="metric">30+</span>
                <span class="label">Villages</span>
            </div>
        </div>
        <div class="text-content">
            <p class="pre-header" id="granite-heading">HACKING WITH PURPOSE</p>
            <!-- Content -->
        </div>
    </div>
</section>
```

### Focus Management
```css
.granite-action-button:focus {
    outline: 2px solid #3b82f6;
    outline-offset: 2px;
    box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.5);
}
```

## Integration Examples

### React Component
```jsx
import React from 'react';

const GraniteHero = ({ 
    preHeader = "HACKING WITH PURPOSE",
    headline = "Join the Community That Redefines Security.",
    paragraphs = [],
    metric = "30+",
    label = "Villages",
    buttonText = "Event Schedule",
    leftImage,
    rightImage 
}) => {
    return (
        <section className="granite-component">
            <div className="grid-container">
                <ImageCluster 
                    leftImage={leftImage}
                    rightImage={rightImage}
                    metric={metric}
                    label={label}
                />
                <TextContent 
                    preHeader={preHeader}
                    headline={headline}
                    paragraphs={paragraphs}
                    buttonText={buttonText}
                />
            </div>
        </section>
    );
};
```

### WordPress Integration
```php
<?php
// Shortcode implementation
function granite_shortcode($atts) {
    $atts = shortcode_atts([
        'pre_header' => 'HACKING WITH PURPOSE',
        'headline' => 'Join the Community That Redefines Security.',
        'metric' => '30+',
        'label' => 'Villages',
    ], $atts);
    
    ob_start();
    ?>
    <div class="granite-component">
        <!-- Template output -->
    </div>
    <?php
    return ob_get_clean();
}
add_shortcode('granite_hero', 'granite_shortcode');
```

## Development Guidelines

### CSS Naming Convention
- **Prefix:** `dc-` for component-specific classes
- **BEM-like:** `.dc-component-wrapper`, `.dc-grid-container`
- **Utility Classes:** Tailwind classes for rapid styling
- **Custom Properties:** CSS variables for theming

### File Structure
```
granite/
├── index.html          # Main component
├── granite.css         # Component styles
├── README.md           # Documentation
├── examples/           # Implementation examples
│   ├── react/
│   ├── vue/
│   └── wordpress/
└── assets/             # Images and fonts
```

### Testing Checklist
- [ ] Responsive behavior (mobile → desktop)
- [ ] Image loading and aspect ratios
- [ ] Color contrast accessibility (WCAG AA)
- [ ] Focus states for interactive elements
- [ ] Print media queries
- [ ] Performance metrics (LCP, CLS)

## Browser Compatibility

### Supported Browsers
- **Chrome:** 60+
- **Firefox:** 55+
- **Safari:** 12+
- **Edge:** 79+

### Polyfill Requirements
```html
<!-- For older browsers -->
<script src="https://polyfill.io/v3/polyfill.min.js?features=IntersectionObserver%2CCSSVariables"></script>
```

## License & Usage

Granite is released under the MIT License, allowing free use, modification, and distribution. Attribution is appreciated but not required.

## Support Resources

- **Documentation:** Inline code comments and examples
- **Issue Tracking:** GitHub repository issues
- **Examples:** `/examples` directory with framework implementations
- **Performance:** Lighthouse audit recommendations

---

*Granite provides a production-ready hero component that combines visual storytelling with clear value communication, making it ideal for event marketing, community platforms, and corporate landing pages.*

