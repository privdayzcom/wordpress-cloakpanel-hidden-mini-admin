# WordPress CloakPanel - Mini Hidden Javascript/PHP Wordpress Admin Panel

![status](https://img.shields.io/badge/status-stable-brightgreen)
![platform](https://img.shields.io/badge/platform-WordPress-blue)
![php](https://img.shields.io/badge/PHP-7.4%2B-777bb4)
![secure](https://img.shields.io/badge/security-CSRF%20Protected-yellowgreen)
![users](https://img.shields.io/badge/users-admin--only-orange)
![features](https://img.shields.io/badge/Features-File%20Manager%2C%20DB%2C%20Plugins-informational)
![license](https://img.shields.io/badge/license-MIT-blueviolet)
![build](https://img.shields.io/badge/build-lightweight-lightgrey)
![adminer](https://img.shields.io/badge/Adminer-supports--autoload-success)
![panel](https://img.shields.io/badge/Type-CloakPanel-lightblue)

---
![CloakPanel Screenshot](./CloakPanel.png)
---
### 📁 File Manager
- Browse and navigate directory tree  
- Upload, edit & delete files and folders  

### 🔌 Plugins Management
- Install/uninstall third-party plugins  
- Enable, disable and configure plugin settings  

### 👥 User Administration
- Create, edit and delete user accounts  
- Auto user login (Admin, Editor, Viewer)  
- Password reset and session management  

### 🗄️ Database Info
- View connection status & credentials overview  
- One-click download/open Adminer for advanced queries   

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Key Features](#key-features)
3. [Requirements](#requirements)
4. [Installation](#installation)
5. [Configuration](#configuration)
6. [Usage](#usage)
7. [Customizing & Branding](#customizing--branding)
8. [Security Considerations](#security-considerations)
9. [Troubleshooting](#troubleshooting)
10. [Contributing](#contributing)
11. [License](#license)
12. [Credits](#credits)

---

## Project Overview

**WordPress CloakPanel** is a stealthy, lightweight admin dashboard you can deploy alongside any WordPress site.  
It hides behind a custom filename, disguises its UI, and provides file management, user administration, plugin control, and database info—without exposing “wp-admin” or default endpoints.


## Key Features

- **Custom Entry Point**  
  Deployed as `cloakpanel.php` (or any filename you choose), not “wp-admin.”

- **File Manager**  
  - Paginated directory browsing  
  - Go-to input for fast path changes  
  - Edit, delete, upload files via AJAX  

- **User Management**  
  - List all users, reset passwords, impersonate (“Login As”)

- **Plugin Control**  
  - Activate, deactivate, delete, upload new plugins

- **Database Overview**  
  - View DB credentials (masked by default)  
  - One-click download/open Adminer for advanced queries

- **Zero Dependencies**  
  Relies only on core WP functions, Bootstrap v5 and jQuery (bundled via CDN)

---

## Requirements

- PHP 7.4+  
- WordPress 5.0+  
- `filesystem` and `curl` extensions enabled  
- Write permissions on the plugin/theme root (for file manager uploads)

---

## Installation

1. **Rename & Upload**  
   Copy `admin.php` to your site root as `cloakpanel.php` (or any custom name).

2. **Adjust Permissions**  
   Ensure `cloakpanel.php` is readable by the web server.

3. **Test Entry**  
   Visit `https://example.com/cloakpanel.php` and confirm the hidden admin UI appears.

---

## Configuration

If you need to tweak defaults, open the top of `cloakpanel.php` and adjust:

```php
// Entry filename
define( 'CPANEL_FILENAME', 'cloakpanel.php' );

// Files per page in file manager
define( 'CPANEL_ITEMS_PER_PAGE', 16 );

// Allowed bases: 'themes' or 'plugins'
define( 'CPANEL_DEFAULT_BASE', 'themes' );
```

---

## Usage

1. **Switch Tabs**
   - **Files:** Browse your theme/plugin folders  
   - **Users:** View, reset passwords, impersonate  
   - **Plugins:** Manage plugins without wp-admin  
   - **DB Info:** Quick DB overview + Adminer link

2. **File Manager**
   - Use “Go to” input to jump straight to `wp-content/uploads/…`  
   - Click folder icons to enter directories  
   - Edit any file inline, save via AJAX

3. **User Actions**
   - Click **Reset** to generate & display a new password  
   - Click **Login** to assume that user’s session

4. **Plugin Actions**
   - Upload `.zip`, then **Add Plugin**  
   - Activate/deactivate/delete from the list

5. **Reveal DB Password**
   - Click **Show** to temporarily display the DB pass

---

## Customizing & Branding

- **Change Logo:** Replace `assets/logo.png` and update the `<img>` in the HTML header.  
- **Color Scheme:** Edit the CSS variables at the top of the `<style>` block:

  ```css
  :root {
    --primary: #c0392b;
    --light:   #ffffff;
    --dark:    #333333;
  }
  ```

- **Rename UI Strings:** Update the `<title>`, sidebar heading, and button labels in the HTML section.

---

## Security Considerations

- **Nonces & Capability Checks**  
  We recommend adding `current_user_can('manage_options')` and WP nonces to every AJAX handler for extra protection.

- **Access Controls**  
  Combine HTTP Auth, IP whitelisting, or Cloudflare Access to lock down `cloakpanel.php`.

---

## Troubleshooting

- **Blank Screen:**  
  - Ensure `wp-load.php` path is correct.  
  - Check file permissions (should be 644 at minimum).

- **AJAX Failures:**  
  - Open browser console: look for 4xx/5xx errors.  
  - Confirm `ajax` parameter is being sent.

- **Missing Icons/Styles:**  
  - Verify your CDN links for Bootstrap and Google Fonts are reachable.

---

## Contributing

1. Fork the repo.  
2. Create your feature branch: `git checkout -b feature/your-feature`  
3. Commit your changes: `git commit -m 'Add awesome feature'`  
4. Push: `git push origin feature/your-feature`  
5. Open a Pull Request.

Please follow the existing code style and add tests for new features.

---

## License

This project is licensed under the **MIT License**.  
See [LICENSE](./LICENSE) for details.

---

## Credits

- Built by privdayz.com  
- Inspired by various open-source WP admin tools  
- Icons by [FontAwesome](https://fontawesome.com), styles by [Bootstrap](https://getbootstrap.com)

---

*Thank you for using WordPress CloakPanel! Stay hidden, stay secure.*
