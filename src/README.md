# Frontend (src)

This directory contains the frontend application for Open WebUI, built with SvelteKit and Tailwind CSS.

## Directory Structure

- `app.css` - Global CSS styles
- `app.d.ts` - TypeScript declarations
- `app.html` - Main HTML template
- `tailwind.css` - Tailwind CSS configuration
- `lib/` - Core library components and utilities
- `routes/` - SvelteKit routes

## Core Components

The frontend is organized into several key modules:

### Library (`lib/`)

The `lib` directory contains reusable components, utilities, and type definitions:

- `components/` - UI components organized by feature
  - `admin/` - Admin panel components
  - `channel/` - Chat channel components
  - `chat/` - Chat interface components
  - `common/` - Shared UI components
  - `icons/` - SVG icon components
  - `workspace/` - Workspace-related components
- `apis/` - API client implementations
- `i18n/` - Internationalization support
- `pyodide/` - Python in browser integration
- `stores/` - Svelte stores for state management
- `types/` - TypeScript type definitions
- `utils/` - Utility functions
- `workers/` - Web worker implementations

### Routes (`routes/`)

The `routes` directory follows SvelteKit's file-based routing system, defining the application's URL structure and page components.

## Key Features

The frontend implements several key features:

1. **Multi-Modal Chat Interface** - Text, image, and audio capabilities
2. **Responsive Design** - Optimized for desktop and mobile
3. **RAG Integration** - Connects to backend for document retrieval
4. **Model Management** - Support for various LLM models
5. **Collaboration Tools** - Real-time collaboration features
6. **Customizable UI** - Theming and layout options
7. **Internationalization** - Multi-language support

## Development

The frontend is built with:

- **SvelteKit** - Frontend framework
- **Tailwind CSS** - Utility-first CSS framework
- **TypeScript** - Type-safe JavaScript

For more detailed information about specific components, see the README files in each subdirectory.

## Next Steps

- [Components Documentation](./lib/components/README.md)
- [API Clients](./lib/apis/README.md)
- [State Management](./lib/stores/README.md)
- [Backend Documentation](../backend/README.md)