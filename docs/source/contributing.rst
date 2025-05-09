Contributing to SocDrawer
=========================

Thank you for your interest in contributing to **SocDrawer**!  
We welcome all contributions that help improve the app's stability, performance, and usability.

Getting Started
---------------

To contribute, please follow these basic steps:

1. Fork the repository.
2. Create a new branch from ``main``.
3. Make your changes while adhering to the conventions outlined below.
4. Add or update unit tests where applicable.
5. Submit a pull request with a clear explanation of your changes.

Please read :doc:`installation <installation>` for more detailed information.

Coding Conventions
------------------

To ensure consistency across the codebase, follow these naming and structure conventions:

- All **views** must be named using the ``*_view.dart`` suffix.
- All **controllers** must use the ``*_controller.dart`` suffix.
- All **services** must use the ``*_service.dart`` suffix.

Code Quality
------------

- **Do not** push directly to the ``main`` branch. All changes must be made through pull requests.
- All code must include **unit tests** for any new features or significant changes.
- Keep pull requests focused and avoid bundling unrelated changes together.

Commit Messages
---------------

Use clear and descriptive commit messages. Prefix messages with one of the following where appropriate:

- ``feat:`` for new features
- ``fix:`` for bug fixes
- ``refactor:`` for code refactoring
- ``test:`` for adding or modifying tests
- ``docs:`` for documentation updates

Example: ``feat: add society search to home_view``

Style Guidelines
----------------

- Follow Flutter’s recommended formatting using `dart format .`.
- Use meaningful variable and function names.
- Avoid deeply nested widget trees—split into smaller widgets where needed.

Submitting a Pull Request
-------------------------

When your changes are ready:

- Ensure your code passes all existing tests and linter checks.
- Push your branch to your fork.
- Open a pull request targeting the ``main`` branch.
- Include a description of what you changed and why.

We appreciate your effort and time in helping us make SocDrawer better! 🙌

