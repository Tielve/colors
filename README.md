# Colors App

A simple CRUD web application for storing and managing colors with user authentication. Users can log in, add new colors to their personal collection, and search through their saved colors.

## Technologies Used

- **Backend:** PHP
- **Database:** MySQL
- **Frontend:** HTML, CSS, JavaScript (Vanilla)
- **Server:** Apache (LAMP Stack)

## Features

- User authentication (login/logout)
- Add colors to your personal collection
- Search colors by name
- Session management via cookies

## Setup Instructions

### Prerequisites

- Apache web server
- PHP 7.0+
- MySQL 5.7+

### Database Setup

1. Create a MySQL database named `COP4331`
2. Create the required tables:

```sql
CREATE TABLE Users (
    ID INT AUTO_INCREMENT PRIMARY KEY,
    Login VARCHAR(255) NOT NULL,
    Password VARCHAR(255) NOT NULL,
    firstName VARCHAR(255),
    lastName VARCHAR(255)
);

CREATE TABLE Colors (
    ID INT AUTO_INCREMENT PRIMARY KEY,
    UserId INT NOT NULL,
    Name VARCHAR(255) NOT NULL,
    FOREIGN KEY (UserId) REFERENCES Users(ID)
);
```

3. Copy `api/config.sample.php` to `api/config.php` and update with your MySQL credentials:
   ```bash
   cp api/config.sample.php api/config.php
   ```
4. Edit `api/config.php` with your database credentials

### Installation

1. Clone the repository to your web server's document root
2. Ensure the `api/` directory is accessible to the web server
3. Configure your Apache server to serve the `public/` directory

## Running the Application

1. Start your Apache and MySQL services
2. Navigate to `http://your-server-address/index.html` in your browser
3. Log in with your credentials
4. Once authenticated, you will be redirected to the colors management page where you can:
   - Add new colors using the "Add Color" input field
   - Search for existing colors using the "Search Color" input field

## Project Structure

```
colors/
├── api/
│   ├── config.sample.php # Sample database configuration (copy to config.php)
│   ├── config.php        # Database configuration (not in git)
│   ├── AddColor.php      # API endpoint to add a new color
│   ├── Login.php         # API endpoint for user authentication
│   └── SearchColors.php  # API endpoint to search colors
├── public/
│   ├── css/
│   │   └── styles.css    # Application styles
│   ├── js/
│   │   ├── code.js       # Main application JavaScript
│   │   └── md5.js        # MD5 hashing library
│   ├── index.html        # Login page
│   └── color.html        # Colors management page
├── images/
│   └── background.png    # Background image
└── README.md
```

---

*This README was generated with the assistance of Claude, an AI assistant by Anthropic.*
