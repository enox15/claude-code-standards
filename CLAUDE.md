# Global Coding Standards

## Language
- Python 3.10+ is the primary language
- Use type hints on all function signatures and return types
- Use pathlib for file paths, not os.path
- Use f-strings for string formatting

## Architecture
- Follow Clean Architecture: separate domain, application, infrastructure, and presentation layers
- Dependencies point inward — domain has no external dependencies
- Use dependency injection, never hard-code dependencies
- Interfaces (abstract base classes) define contracts between layers

## SOLID Principles
- Single Responsibility: each class has one reason to change
- Open/Closed: extend behaviour through new classes, not modifying existing ones
- Liskov Substitution: subtypes must be substitutable for their base types
- Interface Segregation: prefer small, focused interfaces over large ones
- Dependency Inversion: depend on abstractions, not concretions

## Design Patterns
- Use Repository pattern for data access
- Use Factory or Builder for complex object creation
- Use Strategy pattern to encapsulate interchangeable behaviours
- Favour composition over inheritance

## Testing
- Follow TDD: write a failing test before writing implementation code
- 100% unit test coverage is mandatory — every function and branch must be tested
- Use pytest-cov to measure coverage; fail the build if coverage drops below 100%
- Test structure: Arrange, Act, Assert
- One assertion per test where practical
- Use pytest as the test framework
- Use unittest.mock for mocking dependencies
- Name tests descriptively: test_should_[expected]_when_[condition]
- Each class should have a corresponding test file (e.g. photo_resizer.py → test_photo_resizer.py)

## Error Handling
- Define custom exception classes for domain-specific errors (e.g. InvalidPhotoFormat, FaceDetectionFailed)
- Use standard Python exceptions for generic errors (ValueError, TypeError, FileNotFoundError)
- Never use bare except clauses
- Always include meaningful error messages
- Log exceptions at the appropriate level before re-raising

## Code Style
- Follow PEP 8
- Maximum line length: 88 characters (Black formatter standard)
- Use Black for formatting, Ruff for linting
- Docstrings on all public classes and functions (Google style)
- Favour small functions — each should do one thing. If a function feels too long, extract a helper
- Favour small classes — each should have a single, clear responsibility. If a class is growing, split it
- No magic numbers — use named constants

## Naming Conventions
- Classes: PascalCase
- Functions and variables: snake_case
- Constants: UPPER_SNAKE_CASE
- Private members: prefix with underscore
- Modules and packages: short, lowercase, snake_case

## Project Structure
```
project_name/
├── src/
│   └── project_name/
│       ├── domain/          # Entities, value objects, domain exceptions
│       ├── application/     # Use cases, services, interfaces
│       ├── infrastructure/  # External integrations, repositories
│       └── presentation/    # CLI, API, or UI entry points
├── tests/
│   ├── unit/
│   ├── integration/
│   └── conftest.py
├── requirements.txt
├── pyproject.toml
├── CLAUDE.md
└── README.md
```

## Git Practices
- Write clear, imperative commit messages (e.g. "Add face detection service")
- Keep commits small and focused on a single change
- Never commit secrets, credentials, or API keys

## Scope of Changes
- Fixes must be limited in scope to the problem described — do not bundle unrelated changes
- Separate problems get separate PRs, even if noticed while working on the original fix
- Reformatting, restyling, and cleanup must go in a dedicated PR, never mixed with a fix or feature
- If you spot an unrelated issue, note it for a follow-up PR rather than addressing it in the current one

## Logging
- Use the logging module, not print statements
- Use appropriate log levels: DEBUG, INFO, WARNING, ERROR, CRITICAL
- Include context in log messages (what was being processed, relevant IDs)
