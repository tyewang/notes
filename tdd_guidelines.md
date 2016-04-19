# General TDD Guidelines

Rules of thumb for TDD

## General
- When first implementing a feature, focus on the test name and make sure it describes what you expect.
- When writing a test, write the smallest, most basic test first. For example, if I was adding a test for a new API, I would probably start with a testing that a 200 is returned.
- When implementing a test, do the smallest amount of work to satisfy the test. If there’s more logic that is needed, then we need a test to drive that out.
- Don’t think of it as “write a test, write implementation”. It’s more “Add to the tests, add to the implementation”. Each improvement doesn’t need to be its own test; you can augment existing tests.
