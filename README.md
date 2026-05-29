# POSCI - Point of Sale & Inventory Management System

A comprehensive **Point of Sale (POS)** and **Inventory Management System** built with PHP and CodeIgniter 3. Designed for managing sales transactions, customer relationships, supplier information, product inventory, and financial tracking.

## Features

### 🏪 Core Functionality
- **Point of Sale (POS)** - Complete sales transaction management
- **Inventory Management** - Product and category tracking
- **Customer Management** - Customer database and relationship management
- **Supplier Management** - Supplier information and management
- **Sales Analytics** - Daily and monthly sales reports
- **Return Management** - Sales returns and purchase returns processing
- **Accounts Receivable** - Track pending payments and customer arrears
- **User Authentication** - Secure login with "Remember Me" functionality

### 📊 Dashboard Features
- Sales overview (daily and monthly)
- Inventory statistics
- Pending payment tracking
- Customer and supplier counts
- Product category overview

### 📁 Modules
- **Penjualan** (Sales) - Sales transaction processing
- **Produk** (Products) - Product inventory management
- **Kategori** (Categories) - Product categorization
- **Pelanggan** (Customers) - Customer information
- **Supplier** - Supplier management
- **Transaksi** (Transactions) - Financial transactions
- **Retur Penjualan** (Sales Returns) - Sales return processing
- **Retur Purchase** (Purchase Returns) - Purchase return processing
- **Tunggakan** (Receivables) - Outstanding payment tracking

## Tech Stack

### Backend
- **Framework**: CodeIgniter 3.x
- **Language**: PHP (5.6.3+)
- **Database**: MySQL/MariaDB

### Frontend
- **Bootstrap** - Responsive UI framework
- **jQuery** - JavaScript library
- **DataTables** - Advanced table management
- **jQuery UI** - Interactive UI components
- **Font Awesome** - Icon library
- **Morris Charts** - Data visualization
- **jQuery Date Picker** - Date selection
- **Date Range Picker** - Date range selection

### Additional Libraries
- **CSV Export** - Export data to CSV format
- **Print Utility** - Print functionality
- **Input Mask** - Input validation and formatting
- **SlimScroll** - Custom scrollbars

## Requirements

- PHP 5.6.3 or higher
- MySQL 5.5+ or MariaDB
- Apache with mod_rewrite enabled
- Composer (for dependency management)

## Installation

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/posci.git
cd posci
```

### 2. Database Setup
```bash
# Create a new database
mysql -u root -p -e "CREATE DATABASE posci;"

# Import the database schema
mysql -u root -p posci < DATABASE\ FILE/posci.sql
```

### 3. Configure the Application
Edit `application/config/config.php`:
```php
$config['base_url'] = 'http://yourdomain.com/posci/';
```

Edit `application/config/database.php`:
```php
$db['default'] = array(
    'hostname' => 'localhost',
    'username' => 'your_db_user',
    'password' => 'your_db_password',
    'database' => 'posci',
    'dbdriver' => 'mysqli',
);
```

### 4. Set Permissions
```bash
chmod -R 755 application/cache
chmod -R 755 application/logs
chmod -R 755 uploads
```

### 5. Enable Mod Rewrite (Optional, for clean URLs)
Ensure `.htaccess` is in place and Apache mod_rewrite is enabled.

## Usage

### Access the Application
Navigate to `http://localhost/posci/` (or your configured domain)

### Default Login Credentials
- **Username**: admin
- **Password**: password0101

⚠️ **IMPORTANT**: Change the default password immediately after first login!

### Navigation
- Dashboard - Overview of key metrics
- Products - Manage inventory and product catalog
- Categories - Organize products
- Customers - Manage customer information
- Suppliers - Manage supplier data
- Sales - Process sales transactions
- Returns - Handle sales/purchase returns
- Receivables - Track outstanding payments
- Transactions - View financial transactions

## Project Structure

```
posci/
├── application/
│   ├── controllers/          # Route handlers and business logic
│   ├── models/               # Database models
│   ├── views/                # UI templates
│   ├── config/               # Configuration files
│   ├── libraries/            # Custom libraries (CSV, Print)
│   ├── helpers/              # Helper functions
│   ├── cache/                # Application cache
│   └── logs/                 # Application logs
├── public/
│   ├── css/                  # Stylesheets
│   ├── js/                   # JavaScripts
│   ├── bootstrap/            # Bootstrap framework
│   ├── plugins/              # jQuery plugins and libraries
│   └── uploads/              # User uploads
├── system/                   # CodeIgniter core framework
├── DATABASE FILE/            # Database backup/schema
└── index.php                 # Application entry point
```

## Configuration

### Environment Setup
Update environment-specific configurations in:
- `application/config/config.php` - Base URL, timezone, etc.
- `application/config/database.php` - Database credentials
- `application/config/constants.php` - Application constants

### Security Recommendations
1. **Change default credentials** - Update admin password
2. **Use environment variables** - Store sensitive credentials in `.env`
3. **Enable HTTPS** - Use SSL/TLS in production
4. **Database backups** - Regular backup schedule
5. **Update dependencies** - Keep CodeIgniter updated

## Database

The project includes a complete database schema in `DATABASE FILE/posci.sql` with the following main tables:
- users - User accounts and authentication
- products - Product inventory
- categories - Product categories
- customers - Customer information
- suppliers - Supplier data
- sales_transactions - Sales records
- purchase_returns - Purchase return records
- sales_returns - Sales return records
- transactions - Financial transactions

## Troubleshooting

### 404 Errors
- Ensure mod_rewrite is enabled in Apache
- Check `.htaccess` file permissions
- Verify base_url configuration

### Database Connection Errors
- Check MySQL is running
- Verify database credentials in `application/config/database.php`
- Ensure database 'posci' exists

### File Permission Errors
- Grant write permissions to `application/cache` and `application/logs`
- Ensure `uploads/` directory is writable

## Performance Optimization

- Enable query caching in production
- Use database indexing on frequently queried columns
- Implement result caching for dashboard data
- Minify CSS and JavaScript assets
- Use CDN for static assets

## Security Considerations

- Sanitize all user input
- Use prepared statements to prevent SQL injection
- Implement rate limiting on login
- Regular security audits
- Keep framework and dependencies updated
- Use strong passwords
- Enable access logs

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Credits

- **Original Developer**: Muhamad Yulianto
- **Source**: CodeAstro.com
- **Framework**: [CodeIgniter](https://codeigniter.com)

## Support

For issues, questions, or feature requests, please open an issue on GitHub.

## Changelog

### Version 1.0.0
- Initial release
- Complete POS and inventory management system
- Sales, returns, and receivables tracking
- Dashboard with analytics

---

**Last Updated**: May 2026  
**Status**: Active
