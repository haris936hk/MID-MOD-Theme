# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Shopify theme called "Horizon" (version 2.1.6) built with a modern component-based architecture using Liquid templates and JavaScript. The theme emphasizes modularity, performance, and customization through the Shopify Theme Editor.

## Core Architecture

### Component System
- Custom web components extend from `Component` class in `assets/component.js`
- Uses Declarative Shadow DOM for encapsulation and hydration (`assets/critical.js`)
- Components use `ref` attributes for child element references
- Event handling is declarative through custom decorators

### Theme Structure
- **`sections/`**: Full-width page components, customizable in Theme Editor via `{% schema %}` tags
- **`blocks/`**: Smaller, nestable components that can be added/removed/reordered
- **`snippets/`**: Reusable code fragments with required `{% doc %}` documentation
- **`assets/`**: JavaScript modules, TypeScript definitions, CSS, and icons
- **`layout/`**: Base theme layout files (`theme.liquid`, `password.liquid`)
- **`templates/`**: Page templates (JSON format with section references)
- **`config/`**: Theme settings schema and data
- **`locales/`**: Translation files

### JavaScript Architecture
- **Component lifecycle**: `assets/component.js` - Base class for custom web components
- **Critical path**: `assets/critical.js` - Declarative Shadow DOM and ResizeNotifier utilities
- **UI Components**: Cart drawer, header menu, predictive search, media gallery
- **Performance**: Section hydration, lazy loading, view transitions
- **Utilities**: Event handling, focus management, scrolling behavior

### CSS Architecture
- Critical CSS handled through component-specific `{% stylesheet %}` tags
- Custom properties for theme settings managed via `snippets/css-variables.liquid`
- Component-scoped styling using shadow DOM

## Development Patterns

### Creating New Components
For merchant-customizable sections:
```liquid
{% schema %}
{
  "name": "Section Name",
  "settings": [...],
  "blocks": [...]
}
{% endschema %}
```

For reusable snippets:
```liquid
{% doc %}
  Description of the snippet's purpose
  @param {type} name - Parameter description
{% enddoc %}
```

### Component Development
- Extend from `Component` class in `assets/component.js`
- Use `ref` attributes for element references
- Implement in TypeScript-aware JavaScript (jsconfig.json configured)
- Follow shadow DOM patterns for encapsulation

### Theme Customization
- Settings configured via `config/settings_schema.json`
- Color schemes, typography, animations, and layout options
- Component blocks can be added/removed/reordered in Theme Editor

## Common Development Tasks

Since this is a Shopify theme, development is primarily done through:
- **Shopify CLI**: For theme development and deployment
- **Theme Editor**: For content and layout customization
- **Local development**: Preview changes using Shopify's development tools

No traditional build commands (npm, webpack, etc.) are present as this follows Shopify's theme architecture.

## Key Integration Points
- **Shopify Cart API**: via cart drawer components (`cart-drawer.js`, `cart-icon.js`)
- **Predictive Search API**: in search components (`predictive-search.js`)
- **Media API**: for gallery and zoom features (`media-gallery.js`, `zoom-dialog.js`)
- **Theme Editor**: customization through `{% schema %}` tags in sections

## Performance Optimizations
- Declarative Shadow DOM for component hydration
- Section-based loading with `section-hydration.js`
- Critical path optimization in `critical.js`
- Lazy loading patterns throughout components
- View transitions for smooth navigation

## Development Best Practices
- Document components with `{% doc %}` tags for parameters and usage
- Use `{% stylesheet %}` and `{% javascript %}` for component-specific code
- Keep critical assets minimal, load others dynamically
- Follow existing patterns for component structure and naming
- Validate schema JSON using TypeScript definitions in `assets/global.d.ts`