# AI Assistant Instructions for Horizon Theme

## Project Overview
This is a Shopify theme built with a component-based architecture using Liquid templates and modern JavaScript. The theme emphasizes modularity, customization through the Shopify Theme Editor, and performance.

## Key Architecture Patterns

### Component System
- Custom web components extend from `Component` class in `assets/component.js`
- Uses Declarative Shadow DOM for encapsulation and hydration (`assets/critical.js`)
- Components use `ref` attributes for child element references
- Event handling is declarative through custom decorators

### Theme Structure
- `sections/`: Full-width page components, customizable in Theme Editor via `{% schema %}` tags
- `blocks/`: Smaller, nestable components that can be added/removed/reordered
- `snippets/`: Reusable code fragments with required `{% doc %}` documentation
- `assets/`: JavaScript modules and critical CSS, other assets loaded dynamically

### JavaScript Modules
- Component lifecycle management: `assets/component.js`
- Performance optimizations: `assets/critical.js`, lazy loading
- UI Components: Cart drawer, header menu, predictive search
- Utilities: ResizeObserver wrapper, event handling, focus management
- Section rendering: `section-renderer.js` for dynamic updates
- Section hydration: `section-hydration.js` for lazy loading sections

### Import Maps & Module Loading
```liquid
<script type="importmap">
  {
    "imports": {
      "@theme/critical": "{{ 'critical.js' | asset_url }}",
      "@theme/component": "{{ 'component.js' | asset_url }}",
      "@theme/utilities": "{{ 'utilities.js' | asset_url }}"
    }
  }
</script>
```
Use `@theme/` aliases when importing modules for consistent pathing.

### CSS Architecture
- Critical CSS in `assets/base.css`
- Component-specific styles use `{% stylesheet %}` tags
- Custom properties for theme settings (`snippets/css-variables.liquid`)

## Development Workflows

### Creating New Components
1. For merchant-customizable sections:
   ```liquid
   {% schema %}
   {
     "name": "Section Name",
     "settings": [...],
     "blocks": [...]
   }
   {% endschema %}
   ```

2. For reusable snippets:
   ```liquid
   {% doc %}
     Description of the snippet's purpose
     @param {type} name - Parameter description
   {% enddoc %}
   ```

### Best Practices
- Document components with `{% doc %}` tags for parameters and usage
- Validate schema JSON using TypeScript definitions in `assets/global.d.ts`
- Use `{% stylesheet %}` and `{% javascript %}` for component-specific code
- Keep critical assets minimal, use modulepreload for key dependencies
- Handle shadow DOM correctly for component state and morphing
- Follow existing patterns for component structure and naming

### Performance Optimizations
- Use Declarative Shadow DOM for component encapsulation
- Lazy hydrate sections with `section-hydration.js`
- Leverage view transitions for smooth navigation
- Prioritize critical path with proper module loading
- Implement custom ResizeObserver for layout performance
- Cache section HTML where appropriate

### Common Patterns
- Cart interactions: See `cart-drawer.js`, `cart-icon.js`
- Search functionality: `predictive-search.js`
- Media handling: `media-gallery.js`, `zoom-dialog.js`
- Performance: `section-hydration.js`, `section-renderer.js`

## Integration Points
- Theme Editor customization through `{% schema %}` tags
- Shopify Cart API via cart drawer components
- Predictive search API in search components
- Media API for gallery and zoom features

## Developer Tools
- Validate schema: Use JSON schemas in `schemas/` directory
- Debug components: Check shadow DOM in devtools
- Test changes: Preview in Theme Editor
- Performance: Monitor critical path in `critical.js`