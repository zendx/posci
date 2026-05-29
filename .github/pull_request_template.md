name: Pull Request
description: Submit a pull request to POSCI
body:
  - type: markdown
    attributes:
      value: |
        Thank you for contributing to POSCI! Please provide details about your pull request.

  - type: textarea
    id: description
    attributes:
      label: Description
      description: Describe your changes
      placeholder: What does this PR do?
    validations:
      required: true

  - type: textarea
    id: changes
    attributes:
      label: Changes Made
      description: List the specific changes
      placeholder: |
        - Changed...
        - Added...
        - Fixed...
    validations:
      required: true

  - type: textarea
    id: related
    attributes:
      label: Related Issues
      description: Link to any related issues (e.g., Closes #123)
      placeholder: Closes #

  - type: dropdown
    id: type
    attributes:
      label: Type of Change
      options:
        - Bug Fix
        - New Feature
        - Enhancement
        - Documentation
        - Code Refactoring
        - Performance Improvement
        - Security Fix
      multiple: true
    validations:
      required: true

  - type: checkboxes
    id: checklist
    attributes:
      label: Checklist
      options:
        - label: I have read the CONTRIBUTING.md file
          required: true
        - label: My code follows the project's code standards
          required: true
        - label: I have performed a self-review
          required: true
        - label: I have tested my changes locally
          required: true
        - label: I have updated documentation if needed
        - label: I have not included credentials or sensitive data
          required: true

  - type: textarea
    id: testing
    attributes:
      label: Testing Instructions
      description: How can reviewers test your changes?
      placeholder: |
        1. Navigate to...
        2. Perform...
        3. Verify...

  - type: textarea
    id: screenshots
    attributes:
      label: Screenshots (if applicable)
      description: Add screenshots for UI changes
