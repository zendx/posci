# POSCI Security Guidelines

## Security Best Practices

### 1. Authentication & Authorization
- **Change Default Credentials**: Immediately change the default admin password after installation
- **Strong Passwords**: Enforce strong password requirements (min 8 characters, mix of uppercase, lowercase, numbers, special chars)
- **Session Management**: Use secure session handling with appropriate timeout settings
- **Access Control**: Implement role-based access control (RBAC) for different user types

### 2. Database Security
- **SQL Injection Prevention**:
  - Always use prepared statements and parameterized queries
  - Use CodeIgniter's Query Builder or parameterized queries
  - Never concatenate user input into SQL queries
  
- **Credentials**:
  - Use environment variables (.env file) for database credentials
  - Never commit database credentials to version control
  - Use different credentials for development, testing, and production

### 3. Input Validation & Sanitization
```php
// Always validate and sanitize user input
$username = escape($this->input->post("username"));
$email = filter_var($input, FILTER_SANITIZE_EMAIL);

// Use CodeIgniter's form validation library
$this->form_validation->set_rules('email', 'Email', 'required|valid_email');
```

### 4. Password Security
- **Hashing**: Use strong password hashing (bcrypt, argon2, not MD5)
  ```php
  // Current (MD5 - NOT RECOMMENDED)
  $password = md5($password);
  
  // Better
  $password = password_hash($password, PASSWORD_BCRYPT);
  ```
- **Storage**: Never store plain-text passwords
- **Transmission**: Always use HTTPS for password transmission

### 5. CSRF Protection
- Implement CSRF tokens for all forms
- Validate tokens on form submission
- Regenerate tokens after login

### 6. HTTPS & Encryption
- **SSL/TLS**: Use HTTPS in production
- **Redirect HTTP to HTTPS**:
  ```php
  if ($_SERVER['HTTPS'] != 'on') {
      redirect('https://' . $_SERVER['SERVER_NAME'] . $_SERVER['REQUEST_URI']);
  }
  ```
- **Sensitive Data**: Encrypt sensitive data at rest

### 7. File Upload Security
- **Validation**:
  ```php
  $config['upload_path'] = './uploads/';
  $config['allowed_types'] = 'gif|jpg|png|pdf';
  $config['max_size'] = 5120; // 5MB
  $config['max_width'] = 2024;
  $config['max_height'] = 2024;
  ```
- **File Storage**: Store uploads outside web root when possible
- **Prevent Execution**: Disable script execution in upload directories

### 8. Error Handling & Logging
- **Production**: Disable detailed error messages in production (set to 0)
- **Logging**: Log security events (failed logins, access attempts, etc.)
- **Monitoring**: Regularly review logs for suspicious activity

### 9. Access Control
- **Directory Permissions**: Appropriate file and directory permissions
  ```bash
  chmod 755 application/
  chmod 600 application/config/database.php
  chmod 755 application/cache
  chmod 755 application/logs
  chmod 755 public/uploads
  ```
- **Web Root**: Prevent direct access to sensitive directories

### 10. Dependencies & Updates
- **Keep Updated**: Regularly update CodeIgniter and all dependencies
- **Vulnerability Scanning**: Use tools to scan for known vulnerabilities
- **Composer**: Keep composer packages updated

### 11. API Security (if applicable)
- **Authentication**: Implement API authentication (tokens, OAuth)
- **Rate Limiting**: Prevent brute force attacks
- **Validation**: Validate all API inputs
- **Versioning**: Maintain API version compatibility

### 12. Data Protection
- **Backup**: Regular database backups
- **Encryption**: Encrypt sensitive fields in database
- **PII**: Handle personally identifiable information carefully
- **GDPR/Privacy**: Comply with privacy regulations

## Configuration Checklist

### Development
- [ ] Set `APP_ENV=development`
- [ ] Enable `APP_DEBUG=true` for error visibility
- [ ] Use local database credentials

### Production
- [ ] Set `APP_ENV=production`
- [ ] Set `APP_DEBUG=false`
- [ ] Use strong database passwords
- [ ] Enable HTTPS
- [ ] Set secure session settings
- [ ] Update default credentials
- [ ] Enable access logs
- [ ] Set up log rotation
- [ ] Configure firewall rules
- [ ] Enable CSRF protection
- [ ] Set secure cookie flags

## Common Vulnerabilities to Avoid

### 1. SQL Injection
```php
// ❌ WRONG
$query = "SELECT * FROM users WHERE email = '" . $_POST['email'] . "'";

// ✅ CORRECT
$query = $this->db->select('*')
    ->from('users')
    ->where('email', $email)
    ->get();
```

### 2. XSS (Cross-Site Scripting)
```php
// ❌ WRONG
<h1><?php echo $_GET['title']; ?></h1>

// ✅ CORRECT
<h1><?php echo htmlspecialchars($title, ENT_QUOTES, 'UTF-8'); ?></h1>
```

### 3. CSRF (Cross-Site Request Forgery)
```php
// Always include CSRF token in forms
<form method="POST" action="">
    <?php echo form_hidden($this->security->get_csrf_token_name(), 
                           $this->security->get_csrf_hash()); ?>
    <!-- form fields -->
</form>
```

### 4. Insecure Deserialization
```php
// ❌ WRONG - Don't unserialize untrusted data
$data = unserialize($_SESSION['data']);

// ✅ CORRECT - Use JSON
$data = json_decode($_SESSION['data'], true);
```

## Security Tools & Resources

- **OWASP**: https://www.owasp.org/
- **CodeIgniter Security Guide**: https://codeigniter.com/user_guide/libraries/security.html
- **PHP Security**: https://www.php.net/manual/en/security.php
- **Composer Audit**: `composer audit`

## Reporting Security Issues

If you discover a security vulnerability, please email security@example.com instead of using the public issue tracker.

---

**Last Updated**: May 2026
