# Contributing to POSCI

Thank you for your interest in contributing to POSCI! This document provides guidelines and instructions for contributing.

## Getting Started

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/YOUR_USERNAME/posci.git
   cd posci
   ```
3. **Add upstream remote**:
   ```bash
   git remote add upstream https://github.com/ORIGINAL_OWNER/posci.git
   ```
4. **Create a feature branch**:
   ```bash
   git checkout -b feature/your-feature-name
   ```

## Development Setup

1. **Install dependencies**:
   ```bash
   composer install
   ```

2. **Configure environment**:
   ```bash
   cp .env.example .env
   # Edit .env with your local database credentials
   ```

3. **Import database**:
   ```bash
   mysql -u root -p posci < DATABASE\ FILE/posci.sql
   ```

4. **Set up permissions**:
   ```bash
   chmod -R 755 application/cache
   chmod -R 755 application/logs
   chmod -R 755 uploads
   chmod -R 755 public/uploads
   ```

## Code Standards

### PHP Code Style
- Follow PSR-2 coding standards
- Use meaningful variable and function names
- Include documentation for complex logic
- Keep functions focused and single-purpose

### Naming Conventions
- **Controllers**: PascalCase (e.g., `ProductController.php`)
- **Models**: PascalCase with `_model` suffix (e.g., `Product_model.php`)
- **Functions**: snake_case (e.g., `get_products()`)
- **Variables**: snake_case (e.g., `$product_id`)
- **Constants**: UPPERCASE with underscores (e.g., `MAX_ITEMS`)

### Documentation
```php
/**
 * Brief description of what the function does
 *
 * @param string $param1 Description of param1
 * @param int $param2 Description of param2
 * @return array Description of return value
 */
public function myFunction($param1, $param2) {
    // Implementation
}
```

## Pull Request Process

1. **Update your branch with latest upstream**:
   ```bash
   git fetch upstream
   git rebase upstream/main
   ```

2. **Commit your changes**:
   ```bash
   git commit -m "feat: add new feature" -m "Detailed description of changes"
   ```
   Use conventional commit format:
   - `feat:` - New feature
   - `fix:` - Bug fix
   - `docs:` - Documentation
   - `style:` - Code style changes
   - `refactor:` - Code refactoring
   - `perf:` - Performance improvements
   - `test:` - Test additions/changes

3. **Push to your fork**:
   ```bash
   git push origin feature/your-feature-name
   ```

4. **Create a Pull Request** on GitHub with:
   - Clear description of changes
   - Related issue numbers (if applicable)
   - Screenshots (for UI changes)
   - Testing instructions

5. **Address review feedback** and push updates

## Testing

Before submitting a PR:
- Test locally with various scenarios
- Verify database migrations work correctly
- Check for PHP errors and warnings
- Test on different browsers (for UI changes)
- Ensure no hardcoded credentials are included

## Reporting Issues

### Bug Reports
Include:
- Detailed description of the issue
- Steps to reproduce
- Expected behavior vs actual behavior
- PHP version and database used
- Error messages or screenshots

### Feature Requests
Include:
- Clear description of the feature
- Use cases and benefits
- Potential implementation approach
- Mockups (if UI-related)

## Code Review Process

- At least one maintainer review required
- All CI checks must pass
- Changes must follow project standards
- Documentation must be updated

## Questions?

- Check existing issues and PRs
- Review documentation
- Open a discussion issue for questions
- Reach out to maintainers

## License

By contributing, you agree that your contributions will be licensed under the same MIT License as the project.

---

Happy contributing! 🎉
