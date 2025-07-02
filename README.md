# Admin_dashboard
I created  admin dashboard  and admin login page.Admin can update their Details with profile picture etc


## 📁 Project Structure

```text
project-root/
├── config/
│   └── config.php                 # DB config & constants (ADMIN_URL, BASE_URL)
├── layouts/
│   ├── header.php                 # HTML <head> + Navbar
│   ├── top.php                    # Layout top (CSS/JS includes)
│   └── footer.php                 # Footer with JS scripts
├── Uploads/
│   ├── default.png                # Default profile pic
│   ├── logo.png                   # Site logo
│   └── [user-uploaded files]
├── vendor/
│   └── autoload.php              # Composer autoloader (PHPMailer, etc.)
├── dashboard.php                 # Admin dashboard page
├── login.php                     # Admin login page
├── logout.php                    # Logout endpoint
├── forget-password.php           # Request password reset
├── reset-password-verify.php     # Reset link verification
├── profile.php                   # Edit profile
├── form.php                      # Content add/edit form
├── table.php                     # Listing table with modals
├── setting.php                   # Site settings (logo, title)
├── invoice.php                   # Invoice preview/print
├── css/ js/ fonts/               # Static assets folders
└── README.md                     # 📄 You are here!



## 🔐 Features & Functionality

### 🔑 User Authentication
- ✅ Login with secure validation & password hashing
- 🔁 Forgot password via email (PHPMailer SMTP)
- 🔒 Reset password with secure token
- 🔓 Logout functionality

### 👤 Profile Management
- 📝 Update name, email, password, and profile picture
- 🔐 Password change with verification
- 🖼️ Default image fallback

### 📊 Dashboard
- 📌 Overview of key stats (e.g., news count, users, categories)
- 📈 Real-time administrative overview

### 🧾 Content Management
- ➕ Add/edit content via dynamic forms (text, color, date, file)
- 📋 Manage items with a searchable table
- 🔍 Modal popups for viewing item details

### ⚙️ Site Settings
- 🖼️ Upload and change logo
- 🏷️ Update headings and status
- ✅ Toggle active/inactive settings

### 🧾 Invoice Generator
- 📑 Detailed invoice page with dynamic data
- 🖨️ Built-in print functionality

---

## 🛡️ Security Features

### ✅ Implemented
- 🔐 `password_hash()` & `password_verify()` for login and password updates
- 🧱 PDO with prepared statements (SQL Injection protection)
- 🌐 Secure session management with `$_SESSION['admin']`
- 📬 PHPMailer for SMTP-based password recovery
- 🖼️ Image upload MIME type validation

### ⚠️ Recommendations
- 🔒 Use `bin2hex(random_bytes(32))` for password reset tokens
- 🧪 Sanitize file names and validate size for uploads
- 🔐 Use environment variables for sensitive credentials (SMTP, DB)
- ⚠️ Add CSRF protection on forms
- 🛑 Disable SSL verify *only* for testing environments
- 🕒 Implement session timeout & rate limiting on login
- 🛡️ Set cookies as `HttpOnly`, `Secure`, and `SameSite=Strict`

---

## 🚀 Tech Stack

| Layer | Tools |
|-------|-------|
| 🧠 Backend | PHP, MySQL (PDO), PHPMailer |
| 🎨 Frontend | HTML, CSS, JavaScript, Bootstrap |
| 🗃️ Database | MySQL |
| 🧰 Libraries | jscolor, Bootstrap Datepicker, Modals |
| 📦 Dependency Manager | Composer |

---

## 🧪 Sample Queries & Techniques

- ✔️ Login:  
  ```php
  $stmt = $pdo->prepare("SELECT * FROM users WHERE email=?");
  $stmt->execute([$email]);
