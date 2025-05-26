# UI Components

This directory contains the UI components used throughout the Open WebUI application. The components are organized by feature and functionality.

## Directory Structure

- `AddConnectionModal.svelte` - Modal for adding new connections
- `AddFilesPlaceholder.svelte` - Placeholder for file upload UI
- `AddServerModal.svelte` - Modal for adding new servers
- `ChangelogModal.svelte` - Modal for displaying changelog
- `NotificationToast.svelte` - Toast notification component
- `OnBoarding.svelte` - Onboarding experience component

### Admin Components (`admin/`)

Components for the admin panel:

- `Evaluations.svelte` - Model evaluation interface
- `Functions.svelte` - Function management interface
- `Settings.svelte` - Application settings interface
- `Users.svelte` - User management interface
- `Evaluations/` - Subcomponents for evaluations
- `Functions/` - Subcomponents for functions

### Channel Components (`channel/`)

Components for chat channels:

- `Channel.svelte` - Main channel component
- `MessageInput.svelte` - Message input component
- `Messages.svelte` - Message display component
- `Navbar.svelte` - Channel navigation bar
- `Thread.svelte` - Thread view component
- `MessageInput/` - Subcomponents for message input
- `Messages/` - Subcomponents for message display

### Common Components (`common/`)

Reusable UI components used throughout the application:

- `Badge.svelte` - Badge component
- `Banner.svelte` - Banner component
- `Checkbox.svelte` - Checkbox input component
- `CodeEditor.svelte` - Code editor component
- `Collapsible.svelte` - Collapsible section component
- `DragGhost.svelte` - Drag and drop ghost element
- `Drawer.svelte` - Slide-out drawer component
- `FileItem.svelte` - File item component
- `FileItemModal.svelte` - File item modal component
- `Folder.svelte` - Folder component
- `Image.svelte` - Image component
- `ImagePreview.svelte` - Image preview component
- `Loader.svelte` - Loading indicator component
- `Marquee.svelte` - Scrolling text component
- `Modal.svelte` - Modal dialog component
- `Pagination.svelte` - Pagination component
- `RichTextInput.svelte` - Rich text editor component
- `SensitiveInput.svelte` - Password/sensitive data input component
- `Sidebar.svelte` - Sidebar navigation component
- `SlideShow.svelte` - Slideshow component
- `Spinner.svelte` - Loading spinner component
- `SVGPanZoom.svelte` - SVG pan and zoom component
- `Switch.svelte` - Toggle switch component
- `Tags.svelte` - Tag input component
- `Tooltip.svelte` - Tooltip component
- `Valves.svelte` - Valves configuration component

### Icon Components (`icons/`)

SVG icon components:

- Various icon components like `ArchiveBox.svelte`, `ArrowDownTray.svelte`, etc.

### Layout Components (`layout/`)

Components for page layout:

- Layout-related components

### Playground Components (`playground/`)

Components for the playground/experimentation area:

- Playground-related components

### Workspace Components (`workspace/`)

Components for the workspace area:

- `common/` - Common workspace components
- `Knowledge/` - Knowledge base components
- `Prompts/` - Prompt management components

## Component Design Principles

The UI components in Open WebUI follow these design principles:

1. **Reusability** - Components are designed to be reusable across different parts of the application
2. **Composability** - Smaller components can be composed to create more complex UI elements
3. **Responsiveness** - Components adapt to different screen sizes
4. **Accessibility** - Components follow accessibility best practices
5. **Theming** - Components support light and dark themes

## Usage Examples

Most components can be imported and used in Svelte files:

```svelte
<script>
  import Button from '$lib/components/common/Button.svelte';
  import Modal from '$lib/components/common/Modal.svelte';
</script>

<Modal title="Example Modal">
  <p>Modal content goes here</p>
  <Button>Close</Button>
</Modal>
```

## Next Steps

- [Common Components](./common/README.md)
- [Channel Components](./channel/README.md)
- [Admin Components](./admin/README.md)
- [Workspace Components](./workspace/README.md)
- [Backend Documentation](../../../backend/README.md)