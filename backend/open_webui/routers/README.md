# API Routers

This directory contains the FastAPI router modules that define the API endpoints for Open WebUI. Each router module focuses on a specific feature area of the application.

## Router Overview

### Audio Processing (`audio.py`)

Endpoints for audio processing:

- Speech-to-text conversion
- Text-to-speech generation
- Audio file handling

### Authentication (`auths.py`)

Endpoints for user authentication:

- Login/logout
- Token management
- API key management
- OAuth integration

### Channels (`channels.py`)

Endpoints for chat channels:

- Channel creation/management
- Channel membership
- Channel settings

### Chats (`chats.py`)

Endpoints for chat conversations:

- Chat session management
- Message history
- Chat settings

### Configuration (`configs.py`)

Endpoints for application configuration:

- System settings
- User preferences
- Feature toggles

### Evaluations (`evaluations.py`)

Endpoints for model evaluations:

- Performance metrics
- Feedback collection
- Comparison tools

### Files (`files.py`)

Endpoints for file management:

- File upload/download
- File metadata
- File permissions

### Folders (`folders.py`)

Endpoints for folder organization:

- Folder creation/management
- Folder structure
- Folder permissions

### Functions (`functions.py`)

Endpoints for function calling:

- Function registration
- Function execution
- Function management

### Groups (`groups.py`)

Endpoints for user groups:

- Group creation/management
- Group membership
- Group permissions

### Images (`images.py`)

Endpoints for image generation and processing:

- Image generation
- Image manipulation
- Image metadata

### Knowledge (`knowledge.py`)

Endpoints for knowledge bases:

- Knowledge base creation/management
- Content indexing
- Query processing

### Memories (`memories.py`)

Endpoints for conversation memory:

- Context management
- Memory retrieval
- Memory settings

### Models (`models.py`)

Endpoints for LLM model management:

- Model listing
- Model configuration
- Model capabilities

### Ollama Integration (`ollama.py`)

Endpoints for Ollama integration:

- Model management
- Generation requests
- Configuration

### OpenAI Integration (`openai.py`)

Endpoints for OpenAI API integration:

- API compatibility layer
- Model mapping
- Request forwarding

### Pipelines (`pipelines.py`)

Endpoints for pipeline processing:

- Pipeline definition
- Pipeline execution
- Pipeline management

### Prompts (`prompts.py`)

Endpoints for prompt templates:

- Prompt creation/management
- Variable substitution
- Prompt categories

### Retrieval (`retrieval.py`)

Endpoints for retrieval augmented generation:

- Document retrieval
- Vector search
- Relevance scoring

### Tasks (`tasks.py`)

Endpoints for background tasks:

- Task management
- Task status
- Task cancellation

### Tools (`tools.py`)

Endpoints for tool integrations:

- Tool registration
- Tool execution
- Tool management

### Users (`users.py`)

Endpoints for user management:

- User registration
- Profile management
- Permission management

### Utilities (`utils.py`)

Utility endpoints:

- Health checks
- Diagnostics
- Miscellaneous helpers

## API Design Principles

The API endpoints in Open WebUI follow these design principles:

1. **RESTful** - Resources are represented as URLs with standard HTTP methods
2. **Consistent** - Similar patterns are used across different endpoints
3. **Versioned** - API versioning ensures backward compatibility
4. **Authenticated** - Most endpoints require authentication
5. **Documented** - OpenAPI/Swagger documentation is available

## Authentication and Authorization

Most API endpoints require authentication. The authentication flow is:

1. Client authenticates via `/api/auth/login` to obtain a JWT token
2. Token is included in subsequent requests in the `Authorization` header
3. Endpoints check permissions based on the user's role and access rights

## Error Handling

API endpoints use standard HTTP status codes:

- `200` - Success
- `201` - Resource created
- `400` - Bad request (client error)
- `401` - Unauthorized (authentication required)
- `403` - Forbidden (insufficient permissions)
- `404` - Resource not found
- `500` - Server error

Error responses include a JSON body with error details.

## Example Endpoint

Here's a simplified example of how an endpoint is defined:

```python
@router.post("/users/", response_model=UserResponse)
async def create_user(
    user_create: UserCreate,
    db: Session = Depends(get_db),
    current_user: User = Depends(get_admin_user)
):
    """
    Create a new user (admin only).
    """
    db_user = Users.get_by_email(db, email=user_create.email)
    if db_user:
        raise HTTPException(status_code=400, detail="Email already registered")
    
    return Users.create(db=db, obj_in=user_create)
```

## API Documentation

When running in development mode, the API documentation is available at `/docs` using Swagger UI.

## Next Steps

- [Models Documentation](../models/README.md)
- [Retrieval Documentation](../retrieval/README.md)
- [Utils Documentation](../utils/README.md)
- [Frontend Components](../../../src/lib/components/README.md)