# Database Models

This directory contains the SQLAlchemy ORM models that define the database schema for Open WebUI. These models represent the core data structures of the application.

## Model Overview

### Authentication Models (`auths.py`)

Models related to authentication and authorization:

- API keys
- Authentication tokens
- Permission records

### Channel Models (`channels.py`)

Models for chat channels:

- Channel definitions
- Channel membership
- Channel settings

### Chat Models (`chats.py`)

Models for chat conversations:

- Chat sessions
- Chat metadata
- Chat settings

### Feedback Models (`feedbacks.py`)

Models for user feedback:

- Message ratings
- Model evaluations
- User feedback

### File Models (`files.py`)

Models for file storage and management:

- Uploaded files
- File metadata
- File permissions

### Folder Models (`folders.py`)

Models for organizing content:

- Folder structure
- Folder permissions
- Folder metadata

### Function Models (`functions.py`)

Models for function calling:

- Function definitions
- Function parameters
- Function execution records

### Group Models (`groups.py`)

Models for user groups:

- Group definitions
- Group membership
- Group permissions

### Knowledge Models (`knowledge.py`)

Models for knowledge bases:

- Knowledge base definitions
- Knowledge base content
- Knowledge base settings

### Memory Models (`memories.py`)

Models for conversation memory:

- Context storage
- Memory settings
- Memory retrieval

### Message Models (`messages.py`)

Models for chat messages:

- Message content
- Message metadata
- Message attachments

### Model Definitions (`models.py`)

Models for LLM model management:

- Model definitions
- Model configurations
- Model capabilities

### Prompt Models (`prompts.py`)

Models for prompt templates:

- Prompt definitions
- Prompt variables
- Prompt categories

### Tag Models (`tags.py`)

Models for content tagging:

- Tag definitions
- Tag relationships
- Tag metadata

### Tool Models (`tools.py`)

Models for tool integrations:

- Tool definitions
- Tool configurations
- Tool usage records

### User Models (`users.py`)

Models for user accounts:

- User profiles
- User preferences
- User roles

## Database Relationships

The models are interconnected through various relationships:

- Users have many Chats
- Chats contain many Messages
- Files belong to Users
- Knowledge bases contain Files
- Groups have many Users
- Channels have many Members (Users)
- Functions can be associated with specific Users

## Schema Evolution

The database schema evolves over time through migrations. The migration files in `open_webui/internal/migrations/` and `open_webui/migrations/versions/` track these changes.

## Model Usage

Models are used throughout the application:

1. **API Endpoints** - Models are used in the router files to handle CRUD operations
2. **Business Logic** - Models encapsulate the application's business rules
3. **Data Validation** - Models define the structure and constraints for data
4. **Relationships** - Models define how different entities relate to each other

## Example Model

Here's a simplified example of how a model is defined:

```python
class User(Base):
    __tablename__ = "users"

    id = Column(String, primary_key=True, default=generate_uuid)
    username = Column(String, unique=True, nullable=False)
    email = Column(String, unique=True, nullable=False)
    hashed_password = Column(String, nullable=True)
    is_active = Column(Boolean, default=True)
    is_superuser = Column(Boolean, default=False)
    created_at = Column(DateTime, default=datetime.utcnow)
    updated_at = Column(DateTime, default=datetime.utcnow, onupdate=datetime.utcnow)

    # Relationships
    chats = relationship("Chat", back_populates="user")
    files = relationship("File", back_populates="user")
```

## Next Steps

- [Routers Documentation](../routers/README.md)
- [Retrieval Documentation](../retrieval/README.md)
- [Utils Documentation](../utils/README.md)
- [Frontend Components](../../../src/lib/components/README.md)