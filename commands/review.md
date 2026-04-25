Perform a thorough code review of the current changes or specified files. Check:

**Correctness**
- Does the code do what it claims to do?
- Are there logic errors or off-by-one mistakes?
- Are all edge cases handled?

**Standards compliance**
- Does it follow the coding standards in CLAUDE.md?
- Are type hints present on all functions?
- Are docstrings present on all public classes and functions?
- Is PEP 8 followed?

**Architecture**
- Does it follow Clean Architecture boundaries?
- Are dependencies pointing inward?
- Is dependency injection used properly?

**Testing**
- Is there 100% unit test coverage?
- Are tests following TDD naming conventions?
- Is each test focused on a single behaviour?
- Are mocks used appropriately?

**Design**
- Are classes and functions small and focused?
- Is there any code duplication?
- Are design patterns applied correctly?
- Is composition favoured over inheritance?

Provide a summary with: must-fix issues, suggestions, and what was done well.
