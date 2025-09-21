# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Theme Information

This is the **Horizon** Shopify theme (version 2.1.6) by Shopify. It's a modern, minimalist e-commerce theme built with Liquid templating language and follows Shopify's standard theme structure.

## Development Commands

Since this is a Shopify theme, development requires the Shopify CLI:

- `shopify theme dev` - Start local development server with live reload
- `shopify theme push` - Deploy theme to Shopify store
- `shopify theme pull` - Pull latest theme from Shopify store
- `shopify theme check` - Validate theme code for errors and best practices
- `shopify theme package` - Create a .zip file for theme distribution

## Architecture Overview

### Core Structure

**Liquid Templates**: This theme uses Shopify's Liquid templating language with the following structure:

- `layout/` - Base template layouts (theme.liquid, password.liquid)
- `templates/` - Page templates (product, collection, cart, etc.)
- `sections/` - Reusable content sections with configurable settings
- `blocks/` - Smaller reusable components that can be used within sections
- `snippets/` - Shared template partials (not included in this theme)

### Key Directories

**Assets** (`assets/`):
- Contains CSS, JavaScript, and image files
- Uses modular JavaScript with ES6 modules
- TypeScript configuration available in `jsconfig.json`
- Critical path: `critical.js` loaded as module with render blocking

**Configuration** (`config/`):
- `settings_schema.json` - Theme customization options in admin
- `settings_data.json` - Current theme settings values

**Localization** (`locales/`):
- Multi-language support with JSON files
- Default English in `en.default.json`
- Schema files for translation management

**Shopify Integration** (`.shopify/`):
- `metafields.json` - Product metafield definitions for enhanced product data

### Theme Architecture Patterns

**Modular Block System**: The theme uses a sophisticated block-based architecture where:
- Sections contain configurable blocks (defined in schema)
- Blocks are reusable components with their own settings
- Examples: `_product-card.liquid`, `_featured-product.liquid`, `_header-menu.liquid`

**Color Scheme System**: Advanced color management through:
- Defined color schemes in `settings_schema.json`
- CSS custom properties generated from theme settings
- Support for primary/secondary buttons, variants, inputs, etc.

**Typography System**: Comprehensive font management with:
- Multiple font families (body, subheading, heading, accent)
- Configurable sizes for all heading levels (H1-H6)
- Text transformation and spacing controls

**Component Naming**: Uses underscore prefix for internal/partial blocks:
- Public blocks: `product-card.liquid`, `featured-collection.liquid`
- Internal blocks: `_product-details.liquid`, `_header-logo.liquid`

### JavaScript Architecture

**ES6 Module System**:
- Uses `type="module"` for modern JavaScript
- Modular components in `assets/` directory
- Examples: `cart-drawer.js`, `product-recommendations.js`, `search-modal.js`

**TypeScript Support**:
- Configured via `assets/jsconfig.json`
- Type checking enabled with `checkJs: true`
- Path mapping with `@theme/*` alias

### Customization System

**Theme Settings**: Extensive customization through `settings_schema.json`:
- Logo and branding settings
- Color schemes and typography
- Layout and animation preferences
- Cart and checkout configuration
- Product display options

**Metafields Integration**: Product enhancement via custom metafields:
- Color and pattern attributes
- Material specifications
- Shape and theme categorization
- Food storage and drinkware properties

## Development Guidelines

**Liquid Templating**: Follow Shopify Liquid conventions:
- Use semantic HTML5 elements
- Implement proper accessibility attributes
- Include proper meta tags and structured data

**CSS/JS Organization**:
- Keep styles modular and component-based
- Use CSS custom properties for theme settings
- Follow ES6+ JavaScript patterns

**Theme Settings**: When adding new features:
- Define schema in `settings_schema.json`
- Use appropriate input types (color_scheme, range, select, etc.)
- Include proper localization keys

**Performance**: Theme includes performance optimizations:
- Critical CSS and JS loading strategies
- Image optimization through Shopify's image_url filters
- View transitions for smooth navigation