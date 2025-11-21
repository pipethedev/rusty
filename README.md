# rustapi

[![Tests](https://github.com/ndelvalle/rustapi/actions/workflows/test.yml/badge.svg?branch=master)](https://github.com/ndelvalle/rustapi/actions/workflows/test.yml)

RESTful API template built with Rust lang. It uses [MongoDB](https://docs.mongodb.com/)
database and [Axum](https://github.com/tokio-rs/axum) HTTP framework.

### Requirements

- [Rust](https://www.rust-lang.org/tools/install)
- [MongoDB](https://docs.mongodb.com/manual/installation/)

### Environment Setup

1. Copy the example environment file:
   ```bash
   cp .env.example .env
   ```

2. Update the `.env` file with your configuration:
   ```bash
   # Environment configuration
   RUN_MODE=development

   # Server configuration
   SERVER__PORT=8080

   # Database configuration
   DATABASE__URI=mongodb://localhost:27017
   DATABASE__NAME=rustapi

   # Authentication configuration
   AUTH__SECRET=your-secret-key-change-in-production

   # Logger configuration
   LOGGER__LEVEL=debug
   ```

**Note:** Environment variables use double underscores (`__`) as separators for nested configuration (e.g., `SERVER__PORT` maps to `server.port`).

**Configuration Priority:**
1. Environment variables (highest priority)
2. `config/local.json` (if exists, git-ignored)
3. `config/{RUN_MODE}.json` (e.g., `config/production.json`)
4. `config/default.json` (lowest priority)

### How to use this template

To use this template as your project starting point, click "Use this template" at the top of this page, or click [here](https://github.com/ndelvalle/rustapi/generate).

### Feature highlights

* Authentication. Based on [jsonwebtoken](https://github.com/Keats/jsonwebtoken)
* Layered configuration. Based on [config-rs](https://github.com/mehcode/config-rs)
* Logs. Based on [tracing](https://github.com/tokio-rs/tracing)
* Error handling
* Pagination
* E2E Tests
* OpenAPI Specification
* CI based on Github actions
* Dependabot configuration

### Project structure

```bash
├── Cargo.lock
├── Cargo.toml
├── README.md
├── config
│   ├── default.json    # Default configuration
│   ├── production.json # Production configuration (Overwrites the default)
│   └── test.json       # Test configuration (Overwrites the default)
├── rustfmt.toml
├── src
│   ├── database.rs
│   ├── errors.rs
│   ├── lib             # Helpers not related to the business model
│   │   ├── authenticate_request.rs
│   │   ├── date.rs
│   │   ├── mod.rs
│   │   ├── models.rs   # Base Database Model trait
│   │   ├── to_object_id.rs
│   │   └── token.rs
│   ├── logger.rs
│   ├── main.rs
│   ├── models
│   │   ├── cat.rs
│   │   ├── mod.rs
│   │   └── user.rs
│   ├── routes
│   │   ├── cat.rs
│   │   ├── mod.rs
│   │   ├── status.rs
│   │   └── user.rs
│   ├── settings.rs
│   └── tests           # E2E Tests
└── test.sh
```

### Test
To run tests make sure MongoDB is up and running.
```
make test
``` 

## Contributing

Contributors are welcome, please fork and send pull requests! If you find a bug
or have any ideas on how to improve this project please submit an issue.
