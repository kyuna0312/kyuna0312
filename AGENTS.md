# AGENTS.md

## Repository Overview

This is a personal landing page repo (`kyuna0312`) containing images and IDE configs. Actual source code lives in separate repositories:
- **kyuna_web** - TypeScript/JavaScript apps
- **dotfiles** - Configuration files
- **InariWrite** - AI comic tooling

---

## Build Commands

### JavaScript/TypeScript

```bash
npm install
npm run build        # production build
npm start            # production server
npm run dev          # development server
npm run lint         # ESLint
npm run typecheck    # TypeScript check
npm test             # all tests
npm test -- path/to/test.spec.ts  # single test file
npm test -- --watch  # watch mode
npm test -- --coverage
```

### Python

```bash
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
ruff check .         # lint
ruff format .        # format
mypy .              # type check
pytest              # tests
pytest path/to/test_file.py -k "test_name"
```

### Go

```bash
go mod download
go build -o binary-name
golangci-lint run
go test ./...
go test -run TestName ./...
```

### Rust

```bash
cargo build
cargo clippy
cargo fmt
cargo test test_name
```

---

## Code Style Guidelines

### General Principles

1. **Clarity over cleverness** - Write code that's easy to understand
2. **Small, focused functions** - Each function does one thing well
3. **Consistent naming** - Use descriptive, consistent names
4. **Fail fast with clear errors** - Provide helpful error messages

### TypeScript/JavaScript

- Use TypeScript strictly with explicit types
- Prefer `interface` over `type` for object shapes
- Use `const` by default, avoid `any`
- Use optional chaining (`?.`) and nullish coalescing (`??`)
- Use arrow functions for callbacks
- Use array methods (`map`, `filter`, `reduce`) over `for` loops

**Imports (external first, then relative):**
```typescript
import { something } from 'external-package';
import { localModule } from './localModule';
```

**Naming:**
- Variables/functions: camelCase
- Classes/Types: PascalCase
- Constants: SCREAMING_SNAKE_CASE
- Files: kebab-case.ts

### Python

- Follow PEP 8, use type hints
- Use f-strings over concatenation
- Use dataclasses for simple data containers

**Naming:**
- Functions/variables: snake_case
- Classes: PascalCase
- Private: _private_function

### Go

- Use `go fmt` for formatting
- Return errors, don't use panic/recover
- Use interfaces for abstraction

### Rust

- Use explicit types
- Use Result for error handling
- Use clippy suggestions

---

## Error Handling

1. **Never silently ignore errors** - Handle or propagate errors
2. **Provide context** - Include meaningful error messages
3. Use `Result<T, E>` pattern (TS/Go/Rust) or throw with context

---

## Testing Guidelines

1. **Test location** - Co-locate with source files or `__tests__/` folder
2. **Naming** - `*.test.ts` or `*_test.py`
3. **AAA pattern** - Arrange, Act, Assert
4. **Test behavior** - Test outcomes, not implementation
5. **Isolation** - Tests should not depend on each other

---

## Git Conventions

- Use conventional commits: `type(scope): description`
- Types: feat, fix, docs, style, refactor, test, chore
- Keep commits small and focused

---

## Security

- Never commit secrets, keys, or credentials
- Use environment variables for sensitive data
- Validate and sanitize all inputs

---

## Project Structure

```
src/
├── components/     # Reusable UI components
├── hooks/          # Custom React hooks
├── lib/            # Utilities
├── pages/          # Route pages
├── services/       # API clients, business logic
└── types/          # TypeScript definitions
```

---

## IDE Configuration

- ESLint/Prettier for TypeScript/JavaScript
- Ruff/Black for Python
- Configure format-on-save
- Use consistent indentation (2 or 4 spaces - follow project)

---

## Dependencies

- Keep dependencies up to date
- Audit: `npm audit` / `pip-audit`
- Remove unused dependencies
- Pin production dependencies

---

## CI/CD

- Run linters and type checkers before tests
- Fail fast on type errors
- Cache dependencies