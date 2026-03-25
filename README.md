# 📝 TaskList Project

A secure task management web application built with Flask, featuring user authentication and password hashing.

## Features

- 🔐 **User Authentication** - Secure registration and login system
- 🔒 **Password Security** - Passwords are hashed using Werkzeug's security functions
- ✅ **Task Management** - Create, read, update, and delete tasks
- 📋 **Task Status** - Mark tasks as completed/incomplete
- 👤 **User-Specific Tasks** - Each user only sees their own tasks
- 🎨 **Clean UI** - Responsive and intuitive user interface
- 💾 **Persistent Storage** - SQLite database for data persistence

## Technologies Used

- **Backend**: Flask 3.1.3
- **Database**: SQLAlchemy 2.0.48 with SQLite
- **Security**: Werkzeug password hashing
- **Frontend**: HTML, CSS (with custom styling)
- **Template Engine**: Jinja2
- **Session Management**: Flask sessions

## Project Structure

```
TaskList Project/
├── main.py                 # Main application with routes, models, and auth
├── requirements.txt        # Python dependencies
├── README.md              # Project documentation
├── instance/
│   └── tasks.db           # SQLite database (auto-generated)
├── static/
│   └── style.css          # Custom CSS styling
└── templates/
    ├── index.html         # Main task list view
    ├── add.html           # Add new task form
    ├── edit.html          # Edit existing task form
    ├── register.html      # User registration form
    └── login.html         # User login form
```

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Parabelleum/tasklist.git
   cd tasklist
   ```

2. **Create a virtual environment** (recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. **Run the application**:
   ```bash
   python main.py
   ```

2. **Open your browser** and navigate to:
   ```
   http://127.0.0.1:5000
   ```

3. **Get started**:
   - Register a new account
   - Log in with your credentials
   - Start managing your tasks!

## Features in Detail

### Authentication System
- **Registration**: Create a new account with a unique username
- **Login**: Secure authentication with password verification
- **Logout**: Clear session and return to login page
- **Protected Routes**: All task pages require authentication

### Task Management
- **Create Tasks**: Add tasks with titles and optional descriptions
- **View Tasks**: See all your tasks in a clean grid layout
- **Edit Tasks**: Modify task details anytime
- **Delete Tasks**: Remove tasks you no longer need
- **Toggle Status**: Mark tasks as complete or incomplete with a single click

### Security Features
- **Password Hashing**: Passwords are never stored in plain text
- **Session Management**: Secure user sessions with Flask
- **User Isolation**: Users can only access their own tasks
- **Input Validation**: Forms validate required fields

## Routes

### Public Routes
- `/register` - User registration page
- `/login` - User login page

### Protected Routes (require authentication)
- `/` - Home page displaying user's tasks
- `/add` - Add a new task
- `/edit/<id>` - Edit an existing task
- `/delete/<id>` - Delete a task
- `/toggle/<id>` - Toggle task completion status
- `/logout` - Log out and clear session

## Database Schema

### User Model
- `id` (Integer, Primary Key)
- `username` (String, max 80 characters, unique, required)
- `password_hash` (String, max 200 characters, required)

### Task Model
- `id` (Integer, Primary Key)
- `title` (String, max 100 characters, required)
- `description` (String, max 200 characters, optional)
- `completed` (Boolean, default: False)
- `user_id` (Integer, Foreign Key to User, required)

## Security Best Practices

This application implements several security best practices:

1. **Password Hashing**: Uses `generate_password_hash()` to securely hash passwords before storage
2. **Password Verification**: Uses `check_password_hash()` to verify credentials without exposing passwords
3. **Session Management**: Flask sessions track authenticated users
4. **Route Protection**: Middleware checks authentication before allowing access to protected routes
5. **User Data Isolation**: Database queries filter by user_id to ensure data privacy

## Configuration

The application uses the following default configurations in `main.py`:
- Secret key for session management
- SQLite database stored in `instance/tasks.db`
- Debug mode enabled for development

**⚠️ Important for Production**:
- Change the `SECRET_KEY` to a secure random value
- Set `debug=False`
- Use a production-grade database (PostgreSQL, MySQL)
- Enable HTTPS
- Implement rate limiting
- Add CSRF protection

## Development

To modify the application:
- **Routes and logic**: Edit `main.py`
- **Styling**: Modify `static/style.css`
- **Templates**: Update HTML files in `templates/`
- **Database models**: Modify the `User` and `Task` classes in `main.py`

## Testing

To test the application:
1. Register a new user account
2. Log in with the credentials
3. Create, edit, and delete tasks
4. Toggle task completion status
5. Log out and verify you cannot access tasks
6. Try logging in with incorrect credentials
7. Attempt to register with a duplicate username

## Contributing

Feel free to fork this project and submit pull requests for any improvements!

## License

This project is open source and available for personal and educational use.

## Acknowledgments

Built as a learning project to demonstrate:
- Flask web framework fundamentals
- User authentication and authorization
- Password security best practices
- Database relationships with SQLAlchemy
- Session management
- CRUD operations