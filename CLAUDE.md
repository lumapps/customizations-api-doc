# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a **documentation repository** for LumApps Customizations API (SDK and CLI). It provides technical documentation for developers who want to extend LumApps sites using JavaScript and CSS customizations.

The documentation is built using **Jekyll** with the `just-the-docs` theme and is organized into markdown files under the `/docs` directory.

## Documentation Structure

The documentation is organized hierarchically:

- **Main entry point**: [docs/index.md](docs/index.md) - Customizations API overview
- **JavaScript API**: [docs/javascript.md](docs/javascript.md) and subdirectory [docs/javascript/](docs/javascript/)
  - API reference: [docs/javascript/api.md](docs/javascript/api.md)
  - Capabilities: [docs/javascript/capabilities.md](docs/javascript/capabilities.md)
  - Best practices: [docs/javascript/best-pratices.md](docs/javascript/best-pratices.md)
  - Development & deployment: [docs/javascript/development-and-deployment.md](docs/javascript/development-and-deployment.md)
  - Use cases: [docs/javascript/use-cases.md](docs/javascript/use-cases.md)
  - FAQ: [docs/javascript/faq.md](docs/javascript/faq.md)
- **CSS API**: [docs/css.md](docs/css.md) and subdirectory [docs/css/](docs/css/)
  - API reference: [docs/css/api.md](docs/css/api.md)
  - Best practices: [docs/css/best-practices.md](docs/css/best-practices.md)
  - Development & deployment: [docs/css/development-and-deployment.md](docs/css/development-and-deployment.md)
  - Use cases: [docs/css/use-cases.md](docs/css/use-cases.md)

## Jekyll Configuration

The site uses Jekyll with the following configuration:
- **Theme**: `pmarsceill/just-the-docs` (remote theme)
- **Config file**: [docs/_config.yml](docs/_config.yml)
- **Site title**: "LumApps Developers"

All markdown files include YAML frontmatter with:
- `layout`: typically `default`
- `title`: page title
- `nav_order`: controls navigation order
- `parent` / `grand_parent`: defines hierarchical navigation
- `has_children`: indicates if the page has child pages

## Key Customizations API Concepts

### JavaScript API
The JavaScript Customizations API is based on callbacks that execute after the LumApps application loads. The main entry point is:

```javascript
window.lumapps.customize(callback, configuration)
```

The callback receives parameters including:
- `targets` - where customizations can be placed (PAGE, HEADER, NAVIGATION, SEARCH_BOX, etc.)
- `placement` - position relative to target (ABOVE, BELOW, LEFT, RIGHT, etc.)
- `components` - reusable LumApps components (Message, Button, Dropdown, etc.)
- `constants` - constant values for component configuration
- `render` - function to render customizations
- `session` - current user session data
- `on` - event subscription
- `api` - Axios instance for AJAX requests
- `addWidgetFilters` - function to add custom filters to widgets
- `addSearchFilters` - function to add custom filters to global search and Ask AI

### CSS API
CSS customizations allow developers to add custom styles to modify the visual appearance of LumApps sites. The API provides supported CSS classes and anchors that remain stable across releases.

### Deployment Model
Customizations are deployed by adding JavaScript/CSS code to the site's `<head>` tag through the LumApps administration UI (Style > Advanced > Head tag HTML).

## Documentation Maintenance Guidelines

When editing documentation:

1. **Preserve frontmatter**: Always maintain the YAML frontmatter structure
2. **Navigation hierarchy**: Keep `parent`, `grand_parent`, and `nav_order` consistent
3. **Code examples**: Include practical JavaScript/CSS examples that demonstrate actual API usage
4. **Security considerations**: When documenting public site features, include security warnings (especially for `shouldRenderOnPublicSites`)
5. **Browser compatibility**: Mention browser support when relevant (LumApps supports latest 2 versions of Chrome, Firefox, Safari, Edge)
6. **Performance impact**: Document performance considerations for customizations (recommended 2-5KB total)
7. **API versioning**: Note when features are deprecated or breaking changes occur

## Recent Updates

Based on recent commits:
- **Search filters functionality added** - New `addSearchFilters` API for global search and Ask AI
- Widget filters functionality added to documentation
- Public sites customization documentation added
- MDI (Material Design Icons) documentation updated
- New targets added to the API
- Search extension result documentation added

## When Working on This Repository

- This is a **documentation-only** repository - no application code or build processes
- Changes are typically updates to markdown files in `/docs`
- Focus on clarity, completeness, and accurate code examples
- Ensure all links between documentation pages are correct
- Validate that YAML frontmatter is properly formatted
- Keep code examples consistent with the latest API version
