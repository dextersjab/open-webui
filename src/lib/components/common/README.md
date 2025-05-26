# Common UI Components

This directory contains reusable UI components that are used throughout the Open WebUI application. These components form the building blocks of the user interface.

## Component Overview

### Basic UI Elements

- `Badge.svelte` - Display badges and tags
- `Banner.svelte` - Display notification banners
- `Checkbox.svelte` - Customized checkbox input
- `Loader.svelte` - Loading indicator
- `Spinner.svelte` - Animated loading spinner
- `Switch.svelte` - Toggle switch control
- `Tooltip.svelte` - Contextual tooltips

### Input Components

- `CodeEditor.svelte` - Code editor with syntax highlighting
- `RichTextInput.svelte` - Rich text editor with formatting
- `SensitiveInput.svelte` - Password/sensitive data input with visibility toggle
- `Tags.svelte` - Tag input and management

### Layout Components

- `Collapsible.svelte` - Expandable/collapsible sections
- `Drawer.svelte` - Slide-out drawer panel
- `Modal.svelte` - Modal dialog overlay
- `Sidebar.svelte` - Application sidebar navigation
- `Pagination.svelte` - Pagination controls for lists

### File Components

- `FileItem.svelte` - File item display
- `FileItemModal.svelte` - Modal for file details
- `Folder.svelte` - Folder display and navigation

### Media Components

- `Image.svelte` - Enhanced image component
- `ImagePreview.svelte` - Image preview with zoom
- `SlideShow.svelte` - Image slideshow
- `SVGPanZoom.svelte` - SVG viewer with pan and zoom

### Interaction Components

- `DragGhost.svelte` - Visual element for drag operations
- `Marquee.svelte` - Scrolling text display
- `Valves.svelte` - Configuration controls for data flow

## Component Design

These components are designed with the following principles:

1. **Consistency** - Consistent styling and behavior across the application
2. **Accessibility** - ARIA attributes and keyboard navigation
3. **Responsiveness** - Adapts to different screen sizes
4. **Theming** - Support for light and dark themes
5. **Reusability** - Props-based configuration for different use cases

## Usage Examples

### Modal Component

The Modal component provides a reusable dialog overlay:

```svelte
<script>
  import Modal from '$lib/components/common/Modal.svelte';
  import Button from '$lib/components/common/Button.svelte';
  
  let showModal = false;
</script>

<Button on:click={() => showModal = true}>Open Modal</Button>

{#if showModal}
  <Modal 
    title="Example Modal"
    on:close={() => showModal = false}
  >
    <p>This is the modal content.</p>
    
    <svelte:fragment slot="footer">
      <Button variant="secondary" on:click={() => showModal = false}>Cancel</Button>
      <Button variant="primary" on:click={handleConfirm}>Confirm</Button>
    </svelte:fragment>
  </Modal>
{/if}
```

### Collapsible Component

The Collapsible component creates expandable/collapsible sections:

```svelte
<script>
  import Collapsible from '$lib/components/common/Collapsible.svelte';
</script>

<Collapsible title="Section Title" initiallyOpen={true}>
  <p>This content can be collapsed/expanded.</p>
</Collapsible>
```

### FileItem Component

The FileItem component displays file information:

```svelte
<script>
  import FileItem from '$lib/components/common/FileItem.svelte';
  
  const file = {
    id: '123',
    name: 'document.pdf',
    size: 1024000,
    type: 'application/pdf',
    created_at: '2023-01-01T12:00:00Z'
  };
</script>

<FileItem 
  file={file}
  on:click={handleFileClick}
  on:delete={handleFileDelete}
/>
```

## Component Props

Most components accept standard HTML attributes plus custom props. For example:

### Modal Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `title` | string | `''` | Modal title |
| `width` | string | `'30rem'` | Modal width |
| `closeOnEsc` | boolean | `true` | Close on Escape key |
| `closeOnOutsideClick` | boolean | `true` | Close when clicking outside |

### Tooltip Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `text` | string | `''` | Tooltip text |
| `position` | string | `'top'` | Tooltip position (top, right, bottom, left) |
| `delay` | number | `200` | Delay before showing (ms) |

## Events

Components emit standard DOM events plus custom events:

- `on:click` - Click event
- `on:change` - Value change event
- `on:close` - Close/dismiss event
- `on:open` - Open/show event

## Slots

Many components provide slots for custom content:

- Default slot - Main content
- `header` - Header content
- `footer` - Footer content
- `icon` - Custom icon

## Next Steps

- [Channel Components](../channel/README.md)
- [Admin Components](../admin/README.md)
- [Workspace Components](../workspace/README.md)
- [Backend Documentation](../../../../backend/README.md)