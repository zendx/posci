name: Bug Report
description: Report a bug or issue with POSCI
title: "[BUG] "
labels: ["bug"]
body:
  - type: markdown
    attributes:
      value: |
        Thank you for reporting a bug! Please provide as much detail as possible to help us resolve it quickly.

  - type: textarea
    id: description
    attributes:
      label: Description
      description: Describe the bug clearly and concisely
      placeholder: What went wrong?
    validations:
      required: true

  - type: textarea
    id: steps
    attributes:
      label: Steps to Reproduce
      description: Exact steps to reproduce the issue
      placeholder: |
        1. Go to...
        2. Click on...
        3. See the error...
    validations:
      required: true

  - type: textarea
    id: expected
    attributes:
      label: Expected Behavior
      description: What should happen?
      placeholder: Describe what you expected to see

  - type: textarea
    id: actual
    attributes:
      label: Actual Behavior
      description: What actually happened?
      placeholder: Describe what you actually see

  - type: dropdown
    id: environment
    attributes:
      label: Environment
      description: Your setup information
      options:
        - PHP 5.6.3
        - PHP 7.0
        - PHP 7.1
        - PHP 7.2
        - PHP 7.3
        - PHP 7.4
        - PHP 8.0+
      multiple: true

  - type: dropdown
    id: database
    attributes:
      label: Database
      options:
        - MySQL 5.5
        - MySQL 5.7
        - MySQL 8.0
        - MariaDB 10.0
        - MariaDB 10.3+

  - type: dropdown
    id: browser
    attributes:
      label: Browser (if UI issue)
      options:
        - Chrome
        - Firefox
        - Safari
        - Edge
        - Other

  - type: textarea
    id: screenshots
    attributes:
      label: Screenshots/Error Messages
      description: Add any screenshots or error messages (paste image or code)

  - type: textarea
    id: logs
    attributes:
      label: Relevant Logs
      description: Paste any relevant error logs from application/logs/
      render: shell

  - type: textarea
    id: additional
    attributes:
      label: Additional Context
      description: Add any other context about the problem
