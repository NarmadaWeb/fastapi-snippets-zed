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

Supercharge your FastAPI development in the [Zed code editor](https://zed.dev/) with this collection of production-ready code snippets. From bootstrapping your app to deploying with **FastAPI Cloud** and `fastapi deploy`, these snippets follow modern best practices and save you time.

## ✨ Features

- **FastAPI Cloud & CLI Ready**: Full support for `fastapi dev`, `fastapi run`, and `fastapi deploy` patterns.
- **Modern Lifespan Handlers**: Uses `@asynccontextmanager` lifespans instead of deprecated `@app.on_event` startup/shutdown handlers.
- **Modern Syntax**: Uses modern Python features like `Annotated` for clear, type-safe code.
- **Pydantic v2 Ready**: Snippets utilize Pydantic v2 conventions like `model_config` and `model_dump()`.
- **Asynchronous by Default**: Prioritizes `async` patterns for high-performance applications.
- **Comprehensive**: Covers basic app setup, security, database models, WebSockets, caching, health probes, and cloud deployments.

## ⚡ New in this Version

This version introduces dedicated support for **FastAPI Cloud**, the official **FastAPI CLI**, and modern lifespan lifecycle management:

- **`fastcloudapp`**: Creates a production-ready FastAPI app instance configured for FastAPI Cloud & CLI with lifespan and CORS.
- **`fastlifespan`**: Sets up an `@asynccontextmanager` lifespan context manager for startup and shutdown event management.
- **`fastcloudhealth`**: Implements standardized `/healthz` (liveness) and `/readyz` (readiness) probe endpoints for zero-downtime cloud deployments.
- **`fastcloudsettings`**: Pydantic Settings configured for cloud environments and secret management.
- **Modernized Existing Snippets**: Refactored `fastasyncdb` and `fastcache` to use modern lifespan handlers, and updated `fastcrud` to Pydantic v2 `model_dump()`.

### Example: `fastcloudapp`

Quickly create a cloud-ready app instance with lifespan:

```python
from contextlib import asynccontextmanager
from fastapi import FastAPI
from fastapi.middleware.cors import CORSMiddleware

@asynccontextmanager
async def lifespan(app: FastAPI):
    # Startup tasks (e.g. connect DB, warmup caches)
    yield
    # Teardown tasks (e.g. close connections)

app = FastAPI(
    title="FastAPI Cloud App",
    description="Production-ready FastAPI app for FastAPI Cloud & CLI.",
    version="0.1.0",
    lifespan=lifespan,
    docs_url="/docs",
    redoc_url="/redoc",
)

app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```

### Example: `fastcloudhealth`

Add zero-downtime liveness and readiness probes:

```python
from fastapi import APIRouter, status

router = APIRouter(tags=["Monitoring"])

@router.get("/healthz", status_code=status.HTTP_200_OK, include_in_schema=False)
async def liveness():
    """Liveness probe to verify the application process is up."""
    return {"status": "healthy"}

@router.get("/readyz", status_code=status.HTTP_200_OK, include_in_schema=False)
async def readiness():
    """Readiness probe to verify external dependencies (e.g. DB, cache) are healthy."""
    return {"status": "ready"}
```

## 📚 Full Snippet Reference

Here is a complete list of all available snippets.

| Prefix              | Name                            | Description                                                                           |
| ------------------- | ------------------------------- | ------------------------------------------------------------------------------------- |
| `fastcloudapp`      | Cloud-Ready FastAPI App         | Creates a production-ready FastAPI app instance configured for FastAPI Cloud & CLI.   |
| `fastlifespan`      | Lifespan Context Manager        | Sets up a modern FastAPI lifespan context manager for startup and shutdown events.    |
| `fastcloudhealth`   | Cloud Health & Readiness Probes | Defines liveness (`/healthz`) and readiness (`/readyz`) probes for cloud deployments. |
| `fastcloudsettings` | FastAPI Cloud Settings          | Manages cloud environment variables and secrets using Pydantic Settings.              |
| `fastapp`           | FastAPI App Instance            | Creates a new FastAPI application instance with rich metadata.                        |
| `fastrouter`        | APIRouter Instance              | Creates a new APIRouter for modular endpoint organization.                            |
| `fastmodel`         | Pydantic Model (v2)             | Defines a Pydantic model with modern validation and schema examples (Pydantic v2).    |
| `fastget`           | GET Endpoint                    | Defines a GET endpoint with path variables, dependencies, and response model.         |
| `fastpost`          | POST Endpoint                   | Defines a POST endpoint with a request body, background tasks, and a 201 status code. |
| `fastcrud`          | Generic CRUD Router             | Creates a generic CRUD router for a SQLAlchemy model.                                 |
| `faststream`        | Streaming Response              | Defines an endpoint that streams data, e.g., for large files or live data.            |
| `fastsettings`      | Pydantic Settings               | Manages application configuration using Pydantic's BaseSettings for env variables.    |
| `fastsecurity`      | JWT Security Setup              | Sets up JWT authentication with token creation and user dependency.                   |
| `fastdep`           | Database Dependency             | Creates a dependency for yielding a database session per request.                     |
| `fastcors`          | CORS Middleware                 | Configures Cross-Origin Resource Sharing (CORS) middleware.                           |
| `fastupload`        | File Upload Endpoint            | Defines an endpoint for handling file uploads.                                        |
| `fastws`            | WebSocket Endpoint              | Defines a basic WebSocket endpoint for real-time communication.                       |
| `fastmiddle`        | Custom Middleware               | Adds custom middleware, e.g., to calculate and add process time to headers.           |
| `fasttest`          | Pytest Test Client              | Sets up a TestClient for use with Pytest to test API endpoints.                       |
| `faststatic`        | Static Files Mounting           | Mounts a directory to serve static files like CSS, JS, and images.                    |
| `fasttemplates`     | Jinja2 Templates                | Configures Jinja2 for rendering HTML templates.                                       |
| `fastdb`            | SQLAlchemy Sync Setup           | Sets up a synchronous SQLAlchemy engine and session maker.                            |
| `fastlimit`         | Rate Limiting                   | Implements API rate limiting using the slowapi library.                               |
| `fastresponse`      | ORJSON Response                 | Uses ORJSONResponse for faster JSON serialization in an endpoint.                     |
| `fasthealth`        | Health Check Endpoint           | Creates a simple health check endpoint, often excluded from public docs.              |
| `fastpage`          | Pagination Helper               | Provides a generic, reusable pagination function and response model.                  |
| `fastbroadcast`     | WebSocket Broadcast Manager     | Creates a manager to handle multiple WebSocket connections for broadcasting.          |
| `fastsqla`          | SQLAlchemy ORM Model            | Defines a SQLAlchemy ORM model class for database table mapping.                      |
| `fastroles`         | Role-Based Access Control       | Implements a flexible dependency for role-based access control (RBAC).                |
| `fastasyncdb`       | Async Database Connection       | Handles the lifecycle of an asynchronous database connection with lifespan.           |
| `fastexcept`        | Custom Exception Handler        | Defines a custom exception and its corresponding handler.                             |
| `fastemail`         | Background Email Sending        | Adds an email sending function to run in the background.                              |
| `fastcache`         | Redis Caching                   | Integrates Redis for caching endpoint responses with lifespan.                        |
| `fastlog`           | Structured Logging              | Configures structured logging using Python's dictConfig.                              |

## 🤝 Contributing

Contributions are welcome! If you have a snippet that you think would be a great addition, please feel free to open a pull request.

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/my-new-snippet`).
3. Add your snippet to `snippets/python.json`.
4. Update this README file to include your new snippet.
5. Open a pull request with a clear description of your changes.

## 📜 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

<div align="center">
  <strong>Happy Coding! 🐍</strong>
</div>
