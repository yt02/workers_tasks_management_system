# Workers Tasks Management System

A Flutter application for managing worker tasks and profiles.

## Features

- Worker Registration
- Worker Login
- Profile Management
- Profile Image Upload

## Development

The application is built using:
- Flutter
- PHP (Backend)
- MySQL (Database)

## File Structure

```
lib/
├── config/
│   └── app_config.dart    # Configuration settings
├── screens/
│   ├── login_screen.dart
│   ├── registration_screen.dart
│   └── profile_screen.dart
└── main.dart
```



## Screenshots

| Login Page                                                                                | Register Page                                                                               | Profile Page           |
| ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |------------------------|
| ![Screenshot_1746952892](https://github.com/user-attachments/assets/06aa404e-0205-4dcd-8ab0-523790c2e15c)| ![Register](https://github.com/user-attachments/assets/85ba7b6c-f422-494f-9ea9-7b60a9ae3ae8)| ![Screenshot_1746863162](https://github.com/user-attachments/assets/03401071-5149-47e2-8a1b-2585eaa4c77d)|




## Getting Started

### Prerequisites

- Flutter SDK (latest version)
- Dart SDK (latest version)
- Android Studio / VS Code
- XAMPP (for local server)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yt02/workers_tasks_management_system.git
```

2. Navigate to the project directory:
```bash
cd workers_tasks_management_system
```

3. Install dependencies:
```bash
flutter pub get
```

4. Set up the local server:
   - Install XAMPP
   - Place the PHP files in the htdocs directory
   - Start Apache and MySQL services
     ![image](https://github.com/user-attachments/assets/9d6094bf-0eef-41b7-9ea4-76fb5f74e787)


   ## Database Setup

   ### Database Structure

   The application uses MySQL database with the following structure:

   ```sql
   CREATE DATABASE IF NOT EXISTS workers_tasks_db;
   USE workers_tasks_db;

   CREATE TABLE IF NOT EXISTS workers (
      id INT AUTO_INCREMENT PRIMARY KEY,
      full_name VARCHAR(100) NOT NULL,
      email VARCHAR(100) NOT NULL UNIQUE,
      password VARCHAR(255) NOT NULL,
      phone VARCHAR(20) NOT NULL,
      address TEXT NOT NULL,
      profile_image VARCHAR(255),
      created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );
   ```

   ### Database Configuration

   1. Open phpMyAdmin in your XAMPP installation
   2. Create a new database named `workers_tasks_db`
   3. Import the SQL file (api/create_workers_table.sql) or run the above SQL commands
   4. The table will be created with the following fields:
      - `id`: Auto-incrementing primary key
      - `full_name`: Worker's full name (required)
      - `email`: Worker's email address (unique, required)
      - `password`: Hashed password (required)
      - `phone`: Contact number (required)
      - `address`: Worker's address (required)
      - `profile_image`: Path to profile image (optional)
      - `created_at`: Timestamp of record creation


5. Run the application:
```bash
flutter run
```

## Project Structure

```
lib/
├── screens/
│   ├── login_screen.dart
│   ├── registration_screen.dart
│   └── profile_screen.dart
├── models/
├── services/
└── main.dart
```

## API Endpoints

The application uses the following API endpoints (configured in `app_config.dart`):
- Login: `$baseUrl/api/login_worker.php`
- Registration: `$baseUrl/api/register_worker.php`

## API Configuration

The application uses a centralized configuration system located in `lib/config/app_config.dart`. This makes it easy to modify the base URL and API endpoints across the application.

### Changing the IP Address

To change the IP address or base URL of the application:

1. Open `lib/config/app_config.dart`
2. Locate the `baseUrl` constant:
```dart
static const String baseUrl = 'http://10.0.2.2';
```
3. Update the IP address to your desired value. For example:
```dart
static const String baseUrl = 'http://192.168.1.100';
```

The configuration class automatically handles:
- API endpoint URLs
- Image URLs
- Path formatting

The application uses `10.0.2.2` as the localhost IP address when running on an Android emulator. This is because:
- `10.0.2.2` is a special alias to your host machine's loopback interface (127.0.0.1) when using Android emulator
- It allows the emulator to access services running on your development machine

For different environments, you'll need to modify the IP address:

1. **Physical Android Device**:
   - Use your computer's local IP address (e.g., `192.168.1.100`)
   - Both your device and computer must be on the same network
   - Find your IP using `ipconfig` (Windows) or `ifconfig` (Linux/Mac)

2. **iOS Simulator**:
   - Use `localhost` or `127.0.0.1` directly
   - No special IP configuration needed

3. **Production Environment**:
   - Replace with your actual server domain/IP
   - Example: `https://api.yourdomain.com`

## Features in Detail

### User Authentication
- **Login Screen**
  - Email validation
  - Password visibility toggle
  - Error handling with user-friendly messages
  - Session persistence

- **Registration Screen**
  - Form validation for all fields
  - Optional profile picture upload
  - Password visibility toggle
  - Phone number validation (digits only)
  - Multiline address input

### Profile Management
- **Profile Screen**
  - Display worker information
  - Profile picture display
  - Session management
  - Secure logout functionality

### Security Features
- Password hashing using SHA1
- Session management using SharedPreferences
- Form validation on both client and server side
- Secure file upload handling
- Input sanitization

### UI/UX Features
- Gradient backgrounds
- Card-based layouts
- Smooth animations
- Loading indicators
- Error message displays
- Responsive design
- Modern form inputs with icons
- Password visibility toggle
- Profile picture upload preview





