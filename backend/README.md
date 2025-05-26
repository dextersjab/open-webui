# Backend

This directory contains the backend server for Open WebUI, built with FastAPI and SQLAlchemy.

## Directory Structure

- `dev.sh` - Development startup script
- `requirements.txt` - Python dependencies
- `start_windows.bat` - Windows startup script
- `start.sh` - Unix startup script
- `open_webui/` - Main backend package

## Core Components

The backend is organized into several key modules:

### Main Application (`open_webui/`)

- `__init__.py` - Package initialization
- `alembic.ini` - Database migration configuration
- `config.py` - Application configuration
- `constants.py` - Constant definitions
- `env.py` - Environment variable handling
- `functions.py` - Function definitions
- `main.py` - Application entry point
- `tasks.py` - Background task handling

### Internal (`open_webui/internal/`)

- `db.py` - Database connection management
- `wrappers.py` - Utility wrappers
- `migrations/` - Database schema migrations

### Models (`open_webui/models/`)

Database models representing the application's data structures:

- `auths.py` - Authentication models
- `channels.py` - Chat channel models
- `chats.py` - Chat conversation models
- `feedbacks.py` - User feedback models
- `files.py` - File storage models
- `folders.py` - Folder organization models
- `functions.py` - Function calling models
- `groups.py` - User group models
- `knowledge.py` - Knowledge base models
- `memories.py` - Memory/context models
- `messages.py` - Chat message models
- `models.py` - LLM model definitions
- `prompts.py` - Prompt template models
- `tags.py` - Tagging models
- `tools.py` - Tool integration models
- `users.py` - User account models

### Retrieval (`open_webui/retrieval/`)

Retrieval Augmented Generation (RAG) functionality:

- `utils.py` - Utility functions
- `loaders/` - Data loaders for different sources
- `vector/` - Vector database connectors
- `web/` - Web search integrations

### Routers (`open_webui/routers/`)

API endpoints for different features:

- `audio.py` - Audio processing endpoints
- `auths.py` - Authentication endpoints
- `channels.py` - Chat channel endpoints
- `chats.py` - Chat conversation endpoints
- `configs.py` - Configuration endpoints
- `evaluations.py` - Model evaluation endpoints
- `files.py` - File management endpoints
- `folders.py` - Folder management endpoints
- `functions.py` - Function calling endpoints
- `groups.py` - User group endpoints
- `images.py` - Image generation endpoints
- `knowledge.py` - Knowledge base endpoints
- `memories.py` - Memory/context endpoints
- `models.py` - Model management endpoints
- `ollama.py` - Ollama integration endpoints
- `openai.py` - OpenAI API integration endpoints
- `pipelines.py` - Pipeline processing endpoints
- `prompts.py` - Prompt template endpoints
- `retrieval.py` - RAG endpoints
- `tasks.py` - Background task endpoints
- `tools.py` - Tool integration endpoints
- `users.py` - User management endpoints
- `utils.py` - Utility endpoints

### Socket (`open_webui/socket/`)

WebSocket functionality for real-time communication:

- `main.py` - WebSocket server implementation
- `utils.py` - WebSocket utilities

### Utils (`open_webui/utils/`)

Utility functions and helpers:

- `access_control.py` - Permission management
- `audit.py` - Audit logging
- `auth.py` - Authentication utilities
- `chat.py` - Chat processing utilities
- `code_interpreter.py` - Code execution utilities
- `filter.py` - Content filtering
- `logger.py` - Logging configuration
- `middleware.py` - HTTP middleware
- `misc.py` - Miscellaneous utilities
- `models.py` - Model management utilities
- `oauth.py` - OAuth integration
- `payload.py` - Request/response payload handling
- `pdf_generator.py` - PDF generation
- `plugin.py` - Plugin system
- `redis.py` - Redis integration
- `response.py` - Response formatting
- `security_headers.py` - Security header management
- `task.py` - Task management
- `tools.py` - Tool integration utilities
- `webhook.py` - Webhook handling

## Key Features

The backend implements several key features:

1. **API Integration** - Connects to Ollama, OpenAI, and other LLM providers
2. **Authentication** - User authentication and authorization
3. **RAG** - Retrieval Augmented Generation for document search
4. **Web Search** - Integration with various search engines
5. **File Management** - Upload, storage, and processing of files
6. **Vector Search** - Semantic search capabilities
7. **WebSockets** - Real-time communication
8. **Background Tasks** - Asynchronous task processing

## Development

The backend is built with:

- **FastAPI** - Web framework
- **SQLAlchemy** - ORM for database access
- **Alembic** - Database migrations
- **Pydantic** - Data validation
- **Redis** - Caching and message broker

## Next Steps

- [Models Documentation](./open_webui/models/README.md)
- [Routers Documentation](./open_webui/routers/README.md)
- [Retrieval Documentation](./open_webui/retrieval/README.md)
- [Frontend Documentation](../src/README.md)