# Lords Love Butter Theme

A premium, performance-optimized Shopify theme for the Lords Love Butter store, designed with modern best practices for accessibility, SEO, and Core Web Vitals.

---

## Table of Contents

- [Features](#features)
- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [Development](#development)
- [Shopify Best Practices](#shopify-best-practices)
- [Performance](#performance)
- [Accessibility](#accessibility)
- [SEO](#seo)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [Support](#support)

---

## Features

✨ **Performance First**
- Optimized Core Web Vitals (LCP, FID, CLS)
- Lazy loading for images and scripts
- CSS-in-JS for critical styles
- Minified and code-split bundles

♿ **Accessibility**
- WCAG 2.1 AA compliance
- Semantic HTML structure
- ARIA labels and roles
- Keyboard navigation support
- Screen reader friendly

🔍 **SEO Optimized**
- JSON-LD structured data
- Meta tags and Open Graph
- Dynamic sitemap generation
- Canonical URLs
- Mobile-first responsive design

🎨 **Design System**
- CSS Custom Properties for theming
- Dark mode support
- Modular component architecture
- Consistent spacing and typography
- Print-friendly styles

📱 **Mobile Optimized**
- Responsive design (mobile-first approach)
- Touch-friendly interface
- Optimized images for all screen sizes
- Fast load times on 4G

🛒 **E-commerce Features**
- Product filtering and sorting
- Wishlist functionality
- Customer reviews
- Related products
- Quick shop
- Cart abandonment protection

---

## Quick Start

### Prerequisites
- Shopify store with admin access
- Shopify CLI ([Install Guide](https://shopify.dev/themes/tools/cli/install))
- Node.js 16+ (optional, for local development)

### Installation

1. **Clone Repository**
   ```bash
   git clone https://github.com/Cozy-ctrl/lordslovebutter-theme.git
   cd lordslovebutter-theme
   ```

2. **Set Up Shopify CLI**
   ```bash
   shopify theme init
   shopify login --store lordslovebutterstore.myshopify.com
   ```

3. **Deploy Theme**
   ```bash
   # Development (live preview)
   shopify theme dev

   # Production
   shopify theme push
   ```

4. **View in Store**
   - Navigate to your Shopify admin
   - Go to Online Store → Themes
   - Set as active theme

---

## Project Structure

```
lordslovebutter-theme/
├── assets/                 # CSS and JavaScript
│   ├── base.css           # Foundation styles and design system
│   ├── components.css     # Component styles
│   ├── utilities.css      # Utility classes
│   ├── theme.js           # Main JavaScript bundle
│   └── [other assets]
├── blocks/                # Block definitions (sections within sections)
├── config/                # Theme configuration
│   ├── settings_schema.json  # Theme settings
│   └── settings_data.json    # Default settings
├── layout/                # Page layouts
│   └── theme.liquid       # Main layout template
├── locales/               # Translations
│   └── en.default.json    # English strings
├── sections/              # Reusable page sections
│   ├── hero.liquid        # Hero section
│   ├── product-list.liquid # Product grid
│   └── [other sections]
├── snippets/              # Reusable components
│   ├── header.liquid      # Header component
│   ├── footer.liquid      # Footer component
│   └── [other snippets]
├── templates/             # Page templates
│   ├── index.json         # Home page configuration
│   ├── product.liquid     # Product detail page
│   └── [other templates]
├── OPTIMIZATION_ROADMAP.md  # Performance optimization guide
├── README.md              # This file
└── .gitignore

```

---

## Development

### Local Development

1. **Start Development Server**
   ```bash
   shopify theme dev --store lordslovebutterstore.myshopify.com
   ```

2. **Code Hot Reload**
   - Files auto-reload in your development theme
   - Preview at provided localhost URL

### Building Assets

```bash
# Watch for CSS/JS changes (if using npm)
npm run watch

# Build for production
npm run build

# Minify assets
npm run minify
```

### Git Workflow

```bash
# Create feature branch
git checkout -b feature/your-feature-name

# Make changes and commit
git add .
git commit -m "Add your feature description"

# Push and create pull request
git push origin feature/your-feature-name
```

---

## Shopify Best Practices

### 1. Theme Development

✅ **DO:**
- Use semantic HTML (main, section, article, nav)
- Write accessible Liquid templates
- Implement responsive design (mobile-first)
- Use CSS variables for theming
- Optimize images for performance
- Cache static assets
- Test across devices and browsers

❌ **DON'T:**
- Use `position: fixed` without testing mobile
- Add fonts without `font-display: swap`
- Load large JavaScript files synchronously
- Use JavaScript when CSS will do
- Forget alt text on images
- Hard-code colors and spacing
- Test only on desktop

### 2. Liquid Template Best Practices

**Use Snippets for Reusability**
```liquid
{% include 'product-card', product: product %}
```

**Implement Fragment Caching**
```liquid
{% cache %}
  {% for product in collection.products limit: 10 %}
    {% include 'product-card' %}
  {% endfor %}
{% endcache %}
```

**Avoid N+1 Queries**
```liquid
{%- assign related = collection.products | where: "handle", product.handle -%}

{%- for product in related -%}
  {%- include 'product-card' -%}
{%- endfor -%}
```

**Use Liquid Filters Efficiently**
```liquid
{{ "Hello World" | downcase | split: " " | first }}
```

### 3. Asset Management

**CSS Organization**
- base.css: Foundation (reset, variables, typography)
- components.css: Buttons, cards, forms
- utilities.css: Spacing, display, layout helpers

**JavaScript Optimization**
- Defer non-critical scripts
- Use `async` for analytics
- Minimize DOM manipulation
- Use event delegation

**Image Optimization**
```liquid
<img
  src="{{ image | image_url: width: 500 }}"
  srcset="{{ image | image_url: width: 300 }} 300w,
          {{ image | image_url: width: 600 }} 600w"
  sizes="(max-width: 48rem) 100vw, 80vw"
  width="1000"
  height="1000"
  alt="{{ image.alt }}"
  loading="lazy">
```

---

## Performance

### Core Web Vitals Targets

| Metric | Target | Current |
|--------|--------|---------|
| LCP (Largest Contentful Paint) | < 2.5s | - |
| FID (First Input Delay) | < 100ms | - |
| CLS (Cumulative Layout Shift) | < 0.1 | - |
| Lighthouse Score | 90+ | - |

### Performance Monitoring

1. **Google PageSpeed Insights**
   - [Test](https://pagespeed.web.dev/) your site
   - Monitor LCP, FID, CLS
   - Review opportunities and diagnostics

2. **WebPageTest**
   - [Advanced testing](https://www.webpagetest.org/)
   - Film strip view
   - Waterfall chart

3. **Shopify Analytics**
   - Monitor store performance
   - Track conversion rates
   - Analyze traffic patterns

---

## Accessibility

### WCAG 2.1 AA Compliance

✅ **Implemented:**
- Semantic HTML structure
- Proper heading hierarchy
- Color contrast ratios (4.5:1 for text)
- Keyboard navigation
- ARIA labels and descriptions
- Skip-to-main-content link
- Focus indicators

### Testing

**Screen Readers**
- Test with NVDA (Windows), JAWS, or VoiceOver (Mac/iOS)
- Verify all interactive elements are accessible
- Check form labels and error messages

**Keyboard Navigation**
- Tab through all interactive elements
- Verify logical tab order
- Test keyboard shortcuts

**Automated Testing**
```bash
# Use axe DevTools browser extension
# Or run automated tests
npm run test:a11y
```

---

## SEO

### On-Page SEO

✅ **Optimized:**
- One H1 per page
- Descriptive meta titles (50-60 chars)
- Meta descriptions (150-160 chars)
- Structured data (JSON-LD)
- Open Graph tags
- Mobile-friendly design
- Fast loading (Core Web Vitals)

### Schema Markup

**Product Schema**
```json
{
  "@context": "https://schema.org/",
  "@type": "Product",
  "name": "Product Name",
  "price": "29.99",
  "currency": "USD",
  "availability": "InStock",
  "brand": { "@type": "Brand", "name": "Lords Love Butter" }
}
```

**Organization Schema**
```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Lords Love Butter",
  "url": "https://lordslovebutterstore.com",
  "logo": "https://lordslovebutterstore.com/logo.png",
  "description": "Natural beef tallow skincare"
}
```

### Testing

- [Google Rich Results Test](https://search.google.com/test/rich-results)
- [Schema.org Validator](https://validator.schema.org/)
- Google Search Console

---

## Troubleshooting

### Theme Won't Deploy

**Solution:**
```bash
# Validate theme
shopify theme check

# Force push (use cautiously)
shopify theme push --force
```

### Styles Not Applying

1. Clear browser cache (Cmd+Shift+R or Ctrl+Shift+R)
2. Check CSS file is loaded (DevTools → Network)
3. Verify CSS selector specificity
4. Check for inline styles overriding

### JavaScript Errors

1. Open browser console (F12)
2. Check for errors and warnings
3. Verify script paths in theme.liquid
4. Check Shopify CLI logs: `shopify theme logs`

### Images Not Optimized

1. Verify image URLs use `image_url` filter
2. Check width/height attributes are set
3. Ensure `loading="lazy"` is present
4. Test with Google PageSpeed Insights

---

## Contributing

### Branch Naming
- `feature/description` - New features
- `fix/description` - Bug fixes
- `docs/description` - Documentation
- `refactor/description` - Code refactoring

### Commit Messages
```
[TYPE] Brief description (50 chars max)

Longer description if needed (72 chars max line width)
- Bullet point 1
- Bullet point 2

Fixes #123
```

### Code Style
- 2-space indentation
- Semantic class names (BEM methodology)
- Meaningful variable names
- Comments for complex logic

---

## Support

### Resources

**Shopify Documentation**
- [Theme Development](https://shopify.dev/themes)
- [Liquid Reference](https://shopify.dev/api/liquid)
- [Theme Store Guidelines](https://shopify.dev/themes/store/requirements)

**Performance**
- [Web Vitals](https://web.dev/vitals/)
- [Lighthouse](https://developers.google.com/web/tools/lighthouse)
- [CWV Guide](https://web.dev/lighthouse-core-web-vitals/)

**Accessibility**
- [WCAG 2.1](https://www.w3.org/WAI/WCAG21/quickref/)
- [ARIA Authoring Guide](https://www.w3.org/WAI/ARIA/apg/)
- [WebAIM](https://webaim.org/)

### Contact

For issues or questions:
1. Check [Optimization Roadmap](./OPTIMIZATION_ROADMAP.md)
2. Review [GitHub Issues](https://github.com/Cozy-ctrl/lordslovebutter-theme/issues)
3. Open a new issue with details

---

## License

© 2025 Lords Love Butter. All rights reserved.

---

## Changelog

### v1.0.0 (2025-11-07)
- Initial theme release
- Optimized CSS architecture with design system
- Mobile-first responsive design
- WCAG 2.1 AA accessibility compliance
- Performance optimization roadmap
- Complete documentation

---

**Last Updated**: 2025-11-07  
**Status**: Active Development  
**Maintainer**: Development Team
