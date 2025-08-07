## Commit Message Guidelines
Use this format:

<type>(optional-scope): short description

### Allowed types
- feat: A new feature being added or removed
- fix: A bug fix
- docs: Documentation only
- refactor: Code change without behavior change
- test: Adding or changing tests
- chore: Maintenance, tools, deps
- ci: CI-related changes (Github Action, pipelines)
- build: Build system changes (nuget packages, Dockerfile, etc.)

### Rules to Follow
- Use present tense: fix bug, not fixed bug.
- Start with a lowercase letter after : (e.g., fix: correct typo).
- Limit the subject to 50 characters if possible.
- Add details in the body if needed.

### Examples

- feat(auth): add Google login support
- fix: handle null token on startup
- refactor: extract user validator class

