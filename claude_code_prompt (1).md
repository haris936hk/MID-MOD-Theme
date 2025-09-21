# Shopify Dawn Theme Customization - MIN + MOD Interior Store

## Project Overview
Transform Shopify Dawn theme into a minimalist, monochrome interior décor dropshipping store. Focus on clean aesthetics, excellent navigation, and performance.

## Design Requirements

### Visual Style
- **Color Palette**: Monochrome only - Black (#000000), White (#ffffff), Grey dividers (#e5e5e5)
- **Typography**: Inter font family
  - ALL headings: `text-transform: uppercase`
  - ALL body text: `text-transform: lowercase`
- **Layout**: Clean, minimal, generous whitespace, no decorative elements

### Navigation Structure
```
Products (dropdown)
├── Shop by Room
│   ├── Living
│   ├── Kitchen
│   ├── Dining
│   ├── Bedroom
│   ├── Study
│   ├── Laundry
│   ├── Bathroom
│   └── Kids Room
├── Shop by Type
│   ├── Vases & Vessels
│   ├── Sculptures & Objects
│   ├── Kitchen & Tableware
│   ├── Trays & Bowls
│   ├── Cushions & Throws
│   ├── Storage & Organisation
│   ├── Accessories
│   └── Plants & Florals
└── Shop by Style
    ├── Modern Contemporary
    ├── Coastal
    ├── Retro
    └── Wabi Sabi
About
Contact
```

## Technical Implementation

### Header & Navigation
- Prominent search box in header
- Clean mega menu for Products dropdown
- Sticky header with minimal design
- Mobile hamburger menu

### Product Features
- **SKU Display**: Show product SKU under title on product pages
- **Accordion Sections**: Use `<details>` for collapsible content:
  - Product Features
  - Care Instructions
  - Supply Chain Info
  - Specifications
- **Image Hover**: Product cards show second image on hover
- **Quick Add**: Button on product cards

### Collection Pages
- **Filtering**: Faceted filters for Room, Type, Style, Price
- **Search**: Prominent search functionality
- **Product Cards**: Minimal styling, price + quick add

### Discount System
- Display message: "Design industry discount available — 20% off"
- Target customers tagged as "Designer"
- Show on product pages and cart

### Performance
- Responsive images with srcset
- Lazy loading for non-critical images
- Defer non-critical JavaScript
- Optimize Core Web Vitals

## Code Quality Standards
- Semantic HTML with proper heading hierarchy
- Accessible design (alt-text, ARIA labels)
- Mobile-first responsive design
- Clean, commented code
- Preserve existing Dawn functionality where possible

## Files to Modify
Focus on these key files:
- `sections/header.liquid` - Navigation and search
- `sections/product-form.liquid` - SKU display and accordions
- `snippets/product-card.liquid` - Hover effects and quick add
- `templates/collection.liquid` - Filtering and layout
- `assets/base.css` - Typography and color overrides
- `config/settings_schema.json` - Theme customization options

## Implementation Priority
1. Typography and color system
2. Header and mega menu navigation
3. Product page SKU and accordions
4. Product card hover effects
5. Collection filtering
6. Discount messaging
7. Performance optimizations

## Success Criteria
- Matches monochrome aesthetic with uppercase/lowercase typography
- Smooth navigation with proper dropdown menus
- Product pages show SKU and collapsible sections
- Collection pages have working filters
- Designer discount system functional
- Mobile responsive and fast loading
- Clean, maintainable code

## Notes
- Work incrementally, test each change
- Maintain Dawn theme's performance benefits
- Ensure all changes are reversible
- Document any custom code added
- Test on mobile and desktop thoroughly