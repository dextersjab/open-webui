# Admin Components

This directory contains components for the administrative interface in Open WebUI. These components provide tools for system administrators to manage users, settings, evaluations, and functions.

## Component Overview

### Main Components

- `Evaluations.svelte` - Interface for model evaluation and feedback management
- `Functions.svelte` - Interface for managing custom functions
- `Settings.svelte` - Interface for system settings and configuration
- `Users.svelte` - Interface for user management

### Subcomponents

#### Evaluations (`Evaluations/`)

Components for model evaluation:

- `FeedbackMenu.svelte` - Menu for managing feedback
- `Leaderboard.svelte` - Leaderboard display for model performance

#### Functions (`Functions/`)

Components for function management:

- `FunctionEditor.svelte` - Editor for creating and editing functions
- `FunctionMenu.svelte` - Menu for function management

## Functionality

### Evaluations Component

The `Evaluations.svelte` component provides tools for evaluating model performance:

- View and analyze user feedback
- Compare model performance
- Track evaluation metrics
- Generate performance reports
- Manage evaluation criteria

#### Feedback Menu

The `FeedbackMenu.svelte` component allows administrators to:

- View detailed feedback from users
- Filter and sort feedback
- Respond to feedback
- Export feedback data

#### Leaderboard

The `Leaderboard.svelte` component displays:

- Model performance rankings
- Comparative metrics
- Performance trends
- User satisfaction scores

### Functions Component

The `Functions.svelte` component provides tools for managing custom functions:

- Create and edit functions
- Test function execution
- Manage function permissions
- Monitor function usage
- Import/export functions

#### Function Editor

The `FunctionEditor.svelte` component allows administrators to:

- Write function code with syntax highlighting
- Define function parameters
- Set function metadata
- Test function execution
- Configure function permissions

#### Function Menu

The `FunctionMenu.svelte` component provides:

- Function listing and organization
- Search and filtering
- Bulk operations
- Import/export functionality

### Settings Component

The `Settings.svelte` component provides access to system configuration:

- General settings
- Authentication settings
- Model settings
- Integration settings
- Security settings
- Performance settings
- UI/UX settings
- Storage settings
- Notification settings

### Users Component

The `Users.svelte` component provides tools for user management:

- User creation and editing
- Role assignment
- Permission management
- Activity monitoring
- Account status management
- Bulk user operations
- User import/export

## Integration with Backend

The admin components interact with several backend APIs:

- `/api/users` - User management
- `/api/groups` - Group management
- `/api/functions` - Function management
- `/api/evaluations` - Evaluation management
- `/api/configs` - System configuration

## State Management

Admin components use several Svelte stores:

- `userStore` - Manages user data
- `settingsStore` - Handles system settings
- `functionStore` - Manages function data
- `evaluationStore` - Handles evaluation data

## Access Control

Admin components are protected by role-based access control:

- Only users with admin privileges can access these components
- Some components may have more granular permission requirements
- Actions within components may be restricted based on user roles

## Usage Example

Here's a simplified example of how the Users component might be used:

```svelte
<script>
  import Users from '$lib/components/admin/Users.svelte';
  import { userStore } from '$lib/stores/userStore';
  import { onMount } from 'svelte';
  
  let users = [];
  let loading = true;
  let error = null;
  
  onMount(async () => {
    try {
      users = await userStore.getAllUsers();
    } catch (e) {
      error = e.message;
    } finally {
      loading = false;
    }
  });
  
  async function handleUserCreate(userData) {
    await userStore.createUser(userData);
    users = await userStore.getAllUsers();
  }
  
  async function handleUserUpdate(userId, userData) {
    await userStore.updateUser(userId, userData);
    users = await userStore.getAllUsers();
  }
  
  async function handleUserDelete(userId) {
    await userStore.deleteUser(userId);
    users = users.filter(user => user.id !== userId);
  }
</script>

{#if loading}
  <div>Loading...</div>
{:else if error}
  <div class="error">{error}</div>
{:else}
  <Users 
    {users} 
    on:create={e => handleUserCreate(e.detail)}
    on:update={e => handleUserUpdate(e.detail.id, e.detail.data)}
    on:delete={e => handleUserDelete(e.detail)}
  />
{/if}
```

## Data Visualization

Admin components include various data visualization elements:

- Charts for usage statistics
- Graphs for performance metrics
- Tables for data comparison
- Timelines for activity tracking

## Bulk Operations

Many admin components support bulk operations:

- Multi-select interfaces
- Batch processing
- Import/export functionality
- Scheduled operations

## Audit Logging

Admin actions are logged for accountability:

- User action tracking
- Change history
- Audit trails
- Activity timestamps

## Responsive Design

Admin components are designed to be responsive:

- Desktop-optimized interfaces
- Tablet compatibility
- Limited mobile support (admin functions are primarily desktop-focused)

## Next Steps

- [Common Components](../common/README.md)
- [Channel Components](../channel/README.md)
- [Workspace Components](../workspace/README.md)
- [Backend Admin APIs](../../../../backend/open_webui/routers/users.py)