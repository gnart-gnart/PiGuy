---
inclusion: always
---
# Python Standards

## Version

Use the project's explicitly configured supported Python version. Do not assume compatibility with arbitrary Python versions.

## General Style

Write clear, idiomatic Python.

Prefer:
- small functions
- descriptive names
- explicit control flow
- type hints for public interfaces
- standard-library solutions when appropriate
- straightforward data structures

Avoid clever code when a simpler implementation is easier to understand.

## Learning Requirement

When implementing a new algorithmic or data-processing component, prefer solutions that expose the underlying logic rather than hiding it behind a large library.

For example, when a task is specifically intended to practice:
- dictionaries
- sets
- stacks
- queues
- two pointers
- sliding windows
- sorting
- binary search
- trees
- graphs

the implementation should demonstrate the underlying data structure or algorithm. Do not replace a learning exercise with a one-line library call.

## Type Hints

Use type hints for functions that form meaningful module interfaces.

Example:

    def parse_query(line: str) -> DNSQuery:
        ...

Do not add excessive typing complexity merely for the sake of typing.

## Functions

Prefer functions with one clear responsibility. If a function becomes difficult to explain in a few sentences, consider splitting it.

## Exceptions

Catch exceptions only when the application can meaningfully recover, translate, or record the failure. Do not use broad exception handling to hide bugs.

Avoid:

    except Exception:
        pass

## Logging

Use structured, useful logging.

Logs should help answer:
- What happened?
- When did it happen?
- What component failed?
- What input or resource was involved?
- What action was taken?

Never log credentials, tokens, or other secrets.

## Testing

New non-trivial behavior should have tests. Prefer testing behavior and observable outcomes rather than implementation details.

## Code Review

Before considering code complete, verify:
1. Correctness
2. Readability
3. Error handling
4. Test coverage
5. Complexity
6. Security
7. Resource usage