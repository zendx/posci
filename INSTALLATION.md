# Detailed Installation Guide

## System Requirements

- **Operating System**: Linux, Windows, or macOS
- **Web Server**: Apache 2.4+ with mod_rewrite enabled
- **PHP**: 5.6.3 or higher (PHP 7.2+ recommended)
- **Database**: MySQL 5.5+ or MariaDB 10.0+
- **Memory**: Minimum 256MB RAM
- **Disk Space**: Minimum 100MB

### PHP Extensions Required
- MySQLi or PDO
- JSON
- Standard PHP extensions

## Installation Steps

### Step 1: Clone the Repository

```bash
# Clone the repository
git clone https://github.com/yourusername/posci.git
cd posci

# Or download ZIP and extract
```

### Step 2: Database Setup

#### Option A: Using MySQL Command Line

```bash
# Create database
mysql -u root -p -e "CREATE DATABASE posci DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;"

# Import schema
mysql -u root -p posci < DATABASE\ FILE/posci.sql

# Verify
mysql -u root -p -e "USE posci; SHOW TABLES;"
```

#### Option B: Using phpMyAdmin

1. Open phpMyAdmin (http://localhost/phpmyadmin)
2. Click "New Database"
3. Name: `posci`, Collation: `utf8_general_ci`
4. Click "Create"
5. Select `posci` database
6. Go to "Import" tab
7. Select `DATABASE FILE/posci.sql`
8. Click "Import"

#### Option C: Using MySQL Workbench

1. Open MySQL Workbench
2. Create new schema: `posci`
3. Select File → Open SQL Script
4. Choose `DATABASE FILE/posci.sql`
5. Execute script

### Step 3: Environment Configuration

```bash
# Copy environment template
cp .env.example .env

# Edit .env file with your credentials
# Windows
notepad .env

# Linux/macOS
nano .env
```

**Edit these values in `.env`:**
```env
APP_URL=http://localhost/posci/
DB_HOST=localhost
DB_USERNAME=root
DB_PASSWORD=your_password
DB_DATABASE=posci
```

### Step 4: CodeIgniter Configuration

#### Edit `application/config/config.php`

```php
// Set your base URL
$config['base_url'] = 'http://localhost/posci/';
// or for production
$config['base_url'] = 'https://yourdomain.com/';

// Set timezone
$config['time_reference'] = 'UTC';
// or your timezone: 'Asia/Jakarta', 'America/New_York', etc.
```

#### Edit `application/config/database.php`

```php
$db['default'] = array(
    'dsn'   => '',
    'hostname' => 'localhost',  // Your DB host
    'username' => 'root',        // DB username
    'password' => '',            // DB password
    'database' => 'posci',       // DB name
    'dbdriver' => 'mysqli',
    'dbprefix' => '',
    'pconnect' => FALSE,
    'db_debug' => (ENVIRONMENT !== 'production'),
    'cache_on' => FALSE,
    'cachedir' => '',
    'char_set' => 'utf8',
    'dbcollat' => 'utf8_general_ci',
);
```

### Step 5: Set File Permissions

#### Linux/macOS
```bash
# Set directory permissions
chmod -R 755 application/
chmod -R 755 public/
chmod -R 755 system/

# Set write permissions for writable directories
chmod -R 777 application/cache
chmod -R 777 application/logs
chmod -R 777 public/uploads
chmod -R 777 uploads

# Set restrictive permissions for config files
chmod 600 application/config/database.php
chmod 600 application/config/config.php
chmod 600 .env
```

#### Windows
1. Right-click on `application/cache` → Properties
2. Security → Edit → Select Users group
3. Check "Modify" and "Write" → Apply

Repeat for `application/logs`, `uploads/`, and `public/uploads/`

### Step 6: Configure Apache (Optional - for clean URLs)

Ensure `.htaccess` file exists in root. It should contain:

```apache
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteRule ^(.*)$ index.php/$1 [L]
</IfModule>
```

If using XAMPP, enable mod_rewrite:
1. Open `xampp/apache/conf/httpd.conf`
2. Find and uncomment: `LoadModule rewrite_module modules/mod_rewrite.so`
3. Restart Apache

### Step 7: Verify Installation

1. Navigate to `http://localhost/posci/`
2. You should see the login page
3. Login with default credentials:
   - **Username**: admin
   - **Password**: password0101

### Step 8: Initial Setup

After successful login:

1. **Change Admin Password**
   - Go to Profile/Settings
   - Update password immediately
   
2. **Configure System Settings**
   - Set company information
   - Configure business parameters
   
3. **Create Base Data**
   - Add product categories
   - Add suppliers
   - Add initial products
   - Add customers

## XAMPP Setup (Windows)

### Installation on XAMPP

1. **Extract to htdocs**:
   ```
   C:\xampp\htdocs\posci\
   ```

2. **Start XAMPP**:
   - Open XAMPP Control Panel
   - Start Apache
   - Start MySQL

3. **Create Database**:
   - Open http://localhost/phpmyadmin
   - Import `posci.sql`

4. **Configure Files**:
   - Edit `application/config/config.php`
   - Edit `application/config/database.php`
   - Edit `.env`

5. **Set Permissions**:
   - Right-click folders → Properties → Security
   - Give full control to authenticated users

6. **Access Application**:
   - Open http://localhost/posci/

## Production Deployment

### Pre-deployment Checklist

- [ ] Change default admin password
- [ ] Update `$config['base_url']` to production domain
- [ ] Set `ENVIRONMENT = 'production'` in `index.php`
- [ ] Disable debug mode in `application/config/config.php`
- [ ] Review and update database credentials
- [ ] Set up SSL/HTTPS certificate
- [ ] Configure file permissions (755 for dirs, 644 for files)
- [ ] Set up database backups
- [ ] Configure error logging
- [ ] Test all functionality

### Linux Server Deployment

```bash
# Create user and directory
sudo useradd -m posci_user
sudo mkdir -p /var/www/posci
sudo chown posci_user:posci_user /var/www/posci

# Clone repository
cd /var/www/posci
git clone https://github.com/yourusername/posci.git .

# Set permissions
sudo chmod -R 755 application/
sudo chmod -R 777 application/cache
sudo chmod -R 777 application/logs
sudo chmod -R 777 public/uploads
sudo chmod 600 .env application/config/database.php

# Install dependencies
composer install --optimize-autoloader

# Configure database
mysql -u root -p -e "CREATE DATABASE posci;"
mysql -u root -p posci < DATABASE\ FILE/posci.sql
```

## Troubleshooting

### Common Issues and Solutions

#### 404 Not Found Errors
- **Cause**: mod_rewrite not enabled
- **Solution**: 
  - Check Apache mod_rewrite is enabled
  - Verify `.htaccess` file exists
  - Restart Apache

#### Database Connection Error
```
"Unable to connect to your database server"
```
- **Cause**: Wrong database credentials
- **Solution**:
  - Verify `application/config/database.php` settings
  - Check MySQL is running
  - Test credentials in MySQL client

#### Permission Denied Error
```
"Severity: Warning → file_put_contents(...): 
Failed to open stream"
```
- **Cause**: Directory not writable
- **Solution**:
  - Set write permissions on `application/cache` and `application/logs`
  - Check file ownership

#### Blank Page
- **Cause**: PHP error or missing dependencies
- **Solution**:
  - Check error logs: `application/logs/`
  - Enable debug in `config.php`
  - Verify PHP version meets requirements

#### Upload Not Working
- **Cause**: Directory permissions or upload path
- **Solution**:
  - Ensure `public/uploads/` is writable
  - Check upload directory configuration
  - Verify file size limits

## Support Resources

- **CodeIgniter Documentation**: https://codeigniter.com/user_guide/
- **PHP Documentation**: https://www.php.net/docs.php
- **MySQL Documentation**: https://dev.mysql.com/doc/
- **Apache Documentation**: https://httpd.apache.org/docs/

---

**Last Updated**: May 2026
