# 📝 TaskList Project

A simple and elegant task management web application built with Flask and SQLAlchemy.

## Features

- ✅ Create, read, update, and delete tasks
- 📋 Mark tasks as completed/incomplete
- 📝 Add titles and descriptions to tasks
- 🎨 Clean and responsive user interface
- 💾 SQLite database for persistent storage

## Technologies Used

- **Backend**: Flask 3.1.3
- **Database**: SQLAlchemy 2.0.48 with SQLite
- **Frontend**: HTML, CSS (with custom styling)
- **Template Engine**: Jinja2

## Project Structure

```
TaskList Project/
├── main.py                 # Main application file with routes and models
├── requirements.txt        # Python dependencies
├── instance/
│   └── tasks.db           # SQLite database (auto-generated)
├── static/
│   └── style.css          # Custom CSS styling
└── templates/
    ├── index.html         # Main task list view
    ├── add.html           # Add new task form
    └── edit.html          # Edit existing task form
```

## Installation

1. **Clone or download the project**

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

3. **Start managing your tasks!**
   - Click "Add New Task" to create a new task
   - Click the checkbox to mark tasks as complete/incomplete
   - Use "Edit" to modify task details
   - Use "Delete" to remove tasks

## Routes

- `/` - Home page displaying all tasks
- `/add` - Add a new task
- `/edit/<id>` - Edit an existing task
- `/delete/<id>` - Delete a task
- `/toggle/<id>` - Toggle task completion status

## Database Schema

### Task Model
- `id` (Integer, Primary Key)
- `title` (String, max 100 characters, required)
- `description` (String, max 200 characters, optional)
- `completed` (Boolean, default: False)

## Configuration

The application uses the following default configurations in `main.py`:
- Secret key for session management
- SQLite database stored in `instance/tasks.db`
- Debug mode enabled for development

**Note**: For production deployment, make sure to:
- Change the `SECRET_KEY` to a secure random value
- Set `debug=False`
- Use a production-grade database if needed

## Development

To modify the application:
- **Routes and logic**: Edit `main.py`
- **Styling**: Modify `static/style.css`
- **Templates**: Update HTML files in `templates/`

## Contributing

Feel free to fork this project and submit pull requests for any improvements!

## License

This project is open source and available for personal and educational use.