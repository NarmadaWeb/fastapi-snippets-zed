# 🚀 Ultimate FastAPI Snippets for Zed

<div align="center">
  <img src="https://fastapi.tiangolo.com/img/logo-margin/logo-teal.png" alt="FastAPI Logo" width="200"/>
  <br>
  <p>
    <a href="https://marketplace.zed.dev/extensions/fastapi-snippets">
      <img alt="Zed Marketplace" src="https://img.shields.io/badge/Zed-Marketplace-8A2BE2?logo=zed&logoColor=white">
    </a>
    <img alt="Language" src="https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white">
    <img alt="Framework" src="https://img.shields.io/badge/FastAPI-0.100%2B-009688?logo=fastapi&logoColor=white">
  </p>
</div>

Supercharge your FastAPI development in the [Zed code editor](https://zed.dev/) with this collection of production-ready code snippets. From bootstrapping your app to deploying advanced features, these snippets are designed to follow modern best practices and save you time.

## ✨ Features

- **Modern Syntax**: Uses modern Python features like `Annotated` for clear, type-safe code.
- **Comprehensive**: Covers everything from basic app setup to advanced topics like WebSockets, caching, and background tasks.
- **Pydantic v2 Ready**: Snippets are designed to work with the latest Pydantic features.
- **Asynchronous by Default**: Prioritizes `async` patterns for high-performance applications.
- **Well-Documented**: Each snippet comes with a clear description of what it does and how to use it.

## ⚡️ New in this Version

This version introduces powerful new snippets and modernizes existing ones for a better development experience.

- **`fastsettings`**: Manage your application's configuration effortlessly using Pydantic's `BaseSettings`.
- **`fastcrud`**: A generic, reusable router for basic Create, Read, Update, Delete operations with SQLAlchemy.
- **`faststream`**: Implement streaming responses for large data or video feeds.
- **Modernized Snippets**: All existing snippets have been updated to use the latest FastAPI and Pydantic best practices, including `Annotated` type hints and Pydantic v2 `model_config`.

### Example: `fastsettings`
Quickly define and load configuration from environment variables:
```python
from pydantic_settings import BaseSettings, SettingsConfigDict

class Settings(BaseSettings):
    app_name: str = "Awesome API"
    database_url: str
    secret_key: str

    model_config = SettingsConfigDict(env_file=".env")

settings = Settings()
```

### Example: `fastcrud`
Generate a full set of CRUD endpoints for a SQLAlchemy model with a single function:
```python
# In your router file
from . import models, schemas
from .database import get_db

# Create the router
crud_router = create_crud_router(
    prefix="/users",
    tags=["Users"],
    db_session=get_db,
    db_model=models.User,
    schema_read=schemas.UserRead,
    schema_create=schemas.UserCreate,
    schema_update=schemas.UserUpdate,
)

app.include_router(crud_router)
```

## 📚 Full Snippet Reference

Here is a complete list of all available snippets.

| Prefix | Name | Description |
|---|---|---|
| `fastapp` | FastAPI App Instance | Creates a new FastAPI application instance with rich metadata. |
| `fastrouter` | APIRouter Instance | Creates a new APIRouter for modular endpoint organization. |
| `fastmodel` | Pydantic Model (v2) | Defines a Pydantic model with modern validation and schema examples (Pydantic v2). |
| `fastget` | GET Endpoint | Defines a GET endpoint with path variables, dependencies, and response model. |
| `fastpost` | POST Endpoint | Defines a POST endpoint with a request body, background tasks, and a 201 status code. |
| `fastcrud` | Generic CRUD Router | Creates a generic CRUD router for a SQLAlchemy model. |
| `faststream` | Streaming Response | Defines an endpoint that streams data, e.g., for large files or live data. |
| `fastsettings` | Pydantic Settings | Manages application configuration using Pydantic's BaseSettings for env variables. |
| `fastsecurity` | JWT Security Setup | Sets up JWT authentication with token creation and user dependency. |
| `fastdep` | Database Dependency | Creates a dependency for yielding a database session per request. |
| `fastcors` | CORS Middleware | Configures Cross-Origin Resource Sharing (CORS) middleware. |
| `fastupload` | File Upload Endpoint | Defines an endpoint for handling file uploads. |
| `fastws` | WebSocket Endpoint | Defines a basic WebSocket endpoint for real-time communication. |
| `fastmiddle` | Custom Middleware | Adds custom middleware, e.g., to calculate and add process time to headers. |
| `fasttest` | Pytest Test Client | Sets up a TestClient for use with Pytest to test API endpoints. |
| `faststatic` | Static Files Mounting | Mounts a directory to serve static files like CSS, JS, and images. |
| `fasttemplates` | Jinja2 Templates | Configures Jinja2 for rendering HTML templates. |
| `fastdb` | SQLAlchemy Sync Setup | Sets up a synchronous SQLAlchemy engine and session maker. |
| `fastlimit` | Rate Limiting | Implements API rate limiting using the slowapi library. |
| `fastresponse` | ORJSON Response | Uses ORJSONResponse for faster JSON serialization in an endpoint. |
| `fasthealth` | Health Check Endpoint | Creates a simple health check endpoint, often excluded from public docs. |
| `fastpage` | Pagination Helper | Provides a generic, reusable pagination function and response model. |
| `fastbroadcast` | WebSocket Broadcast Manager | Creates a manager to handle multiple WebSocket connections for broadcasting. |
| `fastsqla` | SQLAlchemy ORM Model | Defines a SQLAlchemy ORM model class for database table mapping. |
| `fastroles` | Role-Based Access Control | Implements a flexible dependency for role-based access control (RBAC). |
| `fastasyncdb` | Async Database Connection | Handles the lifecycle of an asynchronous database connection. |
| `fastexcept` | Custom Exception Handler | Defines a custom exception and its corresponding handler. |
| `fastemail` | Background Email Sending | Adds an email sending function to run in the background. |
| `fastcache` | Redis Caching | Integrates Redis for caching endpoint responses. |
| `fastlog` | Structured Logging | Configures structured logging using Python's dictConfig. |

## 🤝 Contributing

Contributions are welcome! If you have a snippet that you think would be a great addition, please feel free to open a pull request.

1.  Fork the repository.
2.  Create a new branch (`git checkout -b feature/my-new-snippet`).
3.  Add your snippet to `snippets/python.json`.
4.  Update this README file to include your new snippet.
5.  Open a pull request with a clear description of your changes.

## 📜 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---
<div align="center">
  <strong>Happy Coding! 🐍</strong>
</div>
