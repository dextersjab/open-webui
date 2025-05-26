# Workspace Components

This directory contains components related to the workspace functionality in Open WebUI. The workspace provides tools for managing knowledge bases, prompts, and other resources that enhance the AI interaction experience.

## Directory Structure

- `common/` - Common workspace components
  - `AccessControl.svelte` - Access control component
  - `AccessControlModal.svelte` - Modal for managing access permissions
  - `ManifestModal.svelte` - Modal for managing manifests
  - `ValvesModal.svelte` - Modal for configuring valves
- `Knowledge/` - Knowledge base components
  - `CreateKnowledgeBase.svelte` - Component for creating knowledge bases
  - `ItemMenu.svelte` - Menu for knowledge base items
  - `KnowledgeBase.svelte` - Main knowledge base component
  - `KnowledgeBase/` - Subcomponents for knowledge bases
    - `AddContentMenu.svelte` - Menu for adding content
    - `AddTextContentModal.svelte` - Modal for adding text content
    - `Files.svelte` - File management component
- `Prompts/` - Prompt management components
  - `PromptEditor.svelte` - Editor for creating and editing prompts
  - `PromptMenu.svelte` - Menu for prompt management

## Core Components

### Common Workspace Components

#### Access Control

The access control components manage permissions for workspace resources:

- `AccessControl.svelte` - Displays and manages access settings
- `AccessControlModal.svelte` - Modal interface for detailed permission management

#### Manifest Management

The manifest components handle resource manifests:

- `ManifestModal.svelte` - Interface for viewing and editing resource manifests

#### Valves Configuration

The valves components manage data flow configuration:

- `ValvesModal.svelte` - Interface for configuring data processing valves

### Knowledge Base Components

Knowledge base components manage document collections for retrieval augmented generation:

#### Knowledge Base Creation

- `CreateKnowledgeBase.svelte` - Interface for creating new knowledge bases with settings

#### Knowledge Base Management

- `KnowledgeBase.svelte` - Main component for interacting with knowledge bases
- `ItemMenu.svelte` - Menu for knowledge base item actions

#### Content Management

- `AddContentMenu.svelte` - Menu for adding different types of content
- `AddTextContentModal.svelte` - Modal for adding text content directly
- `Files.svelte` - Component for managing files within knowledge bases

### Prompt Components

Prompt components manage reusable prompt templates:

#### Prompt Editor

- `PromptEditor.svelte` - Rich editor for creating and editing prompt templates

#### Prompt Management

- `PromptMenu.svelte` - Menu for prompt actions and organization

## Functionality

### Knowledge Base Functionality

The knowledge base components provide these key features:

1. **Document Management** - Upload, organize, and delete documents
2. **Content Extraction** - Extract text and metadata from various file formats
3. **Indexing** - Process documents for vector search
4. **Retrieval** - Search and retrieve relevant information
5. **Access Control** - Manage who can access knowledge bases

### Prompt Functionality

The prompt components provide these key features:

1. **Template Creation** - Create reusable prompt templates
2. **Variable Substitution** - Define variables that can be filled in at runtime
3. **Organization** - Categorize and manage prompt templates
4. **Sharing** - Share prompts with other users
5. **Versioning** - Track changes to prompts

## Integration with Backend

The workspace components interact with several backend APIs:

- `/api/knowledge` - Knowledge base management
- `/api/files` - File management
- `/api/prompts` - Prompt template management

## State Management

Workspace components use several Svelte stores:

- `knowledgeStore` - Manages knowledge base data
- `promptStore` - Handles prompt template data
- `fileStore` - Manages file data
- `userStore` - Provides user information for permissions

## Usage Examples

### Knowledge Base Example

```svelte
<script>
  import KnowledgeBase from '$lib/components/workspace/Knowledge/KnowledgeBase.svelte';
  import { knowledgeStore } from '$lib/stores/knowledgeStore';
  
  // Get knowledge base ID from route params
  export let knowledgeBaseId;
  
  // Load knowledge base data
  $: {
    if (knowledgeBaseId) {
      knowledgeStore.loadKnowledgeBase(knowledgeBaseId);
    }
  }
</script>

<KnowledgeBase id={knowledgeBaseId} />
```

### Prompt Editor Example

```svelte
<script>
  import PromptEditor from '$lib/components/workspace/Prompts/PromptEditor.svelte';
  import { promptStore } from '$lib/stores/promptStore';
  
  // Get prompt ID from route params
  export let promptId;
  
  // Load prompt data
  $: {
    if (promptId) {
      promptStore.loadPrompt(promptId);
    }
  }
</script>

<PromptEditor id={promptId} />
```

## RAG Integration

The knowledge base components integrate with the Retrieval Augmented Generation (RAG) system:

1. Documents are uploaded and processed
2. Text is extracted and chunked
3. Chunks are embedded and stored in vector databases
4. During chat, relevant chunks are retrieved
5. Retrieved information augments the LLM prompt

## File Support

The knowledge base components support various file formats:

- PDF documents
- Word documents
- Text files
- Markdown files
- CSV/Excel files
- HTML files
- And more

## Accessibility

Workspace components implement accessibility features:

- ARIA attributes for screen readers
- Keyboard navigation
- Focus management
- High contrast support

## Next Steps

- [Common Components](../common/README.md)
- [Channel Components](../channel/README.md)
- [Admin Components](../admin/README.md)
- [Backend Knowledge API](../../../../backend/open_webui/routers/knowledge.py)