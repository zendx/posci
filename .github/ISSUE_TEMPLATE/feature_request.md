name: Feature Request
description: Suggest a new feature or enhancement
title: "[FEATURE] "
labels: ["enhancement"]
body:
  - type: markdown
    attributes:
      value: |
        Thank you for suggesting a feature! We'd love to hear your ideas for improving POSCI.

  - type: textarea
    id: description
    attributes:
      label: Feature Description
      description: Describe the feature you'd like to see
      placeholder: What feature would you like?
    validations:
      required: true

  - type: textarea
    id: problem
    attributes:
      label: Problem It Solves
      description: What problem does this feature solve?
      placeholder: Describe the problem or use case

  - type: textarea
    id: solution
    attributes:
      label: Proposed Solution
      description: How do you think this feature should work?
      placeholder: Describe your proposed solution

  - type: textarea
    id: alternatives
    attributes:
      label: Alternative Solutions
      description: Any alternative solutions or features you've considered?

  - type: textarea
    id: context
    attributes:
      label: Additional Context
      description: Add any other screenshots, examples, or context

  - type: checkboxes
    id: checklist
    attributes:
      label: Checklist
      options:
        - label: I have searched existing issues
          required: true
        - label: I have read the documentation
          required: true
