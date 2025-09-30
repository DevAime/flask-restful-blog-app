# Flask Blog Application

A full-featured blog application built with Flask, implementing RESTful routing principles for creating, reading, updating, and deleting blog posts.

## Features

- **Create Posts**: Add new blog posts with rich text editing
- **View Posts**: Browse all blog posts and view individual posts
- **Edit Posts**: Update existing blog posts
- **Delete Posts**: Remove unwanted blog posts
- **Rich Text Editor**: CKEditor integration for formatted content
- **Responsive Design**: Bootstrap 5 for mobile-friendly layouts
- **SQLite Database**: Lightweight database for storing blog posts
- **Environment Variables**: Secure configuration management

## Technologies Used

- **Flask**: Python web framework
- **Flask-SQLAlchemy**: Database ORM
- **Flask-WTF**: Form handling and validation
- **Flask-CKEditor**: Rich text editor integration
- **Flask-Bootstrap**: Bootstrap 5 integration
- **Python-dotenv**: Environment variable management
- **SQLite**: Database engine

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd <repository-name>
```

2. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install flask flask-bootstrap flask-sqlalchemy flask-wtf flask-ckeditor python-dotenv
```

4. Set up environment variables:

Create a `.env` file in the root directory:
```env
SECRET_KEY=your-secret-key-here
DATABASE_URI=sqlite:///posts.db
```

**Important**: Add `.env` to your `.gitignore` file:
```bash
echo ".env" >> .gitignore
```

5. Run the application:
```bash
python main.py
```

6. Open your browser and navigate to:
```
http://localhost:5003
```

## Environment Variables Setup

This application uses `python-dotenv` to manage sensitive configuration securely.

### Configuration Files

Create a `.env` file in the root directory with the following variables:

```env
# Flask secret key for session management and CSRF protection
SECRET_KEY=your-secret-key-here

# Database connection URI
DATABASE_URI=sqlite:///posts.db
```

**Variable Descriptions:**

- `SECRET_KEY`: A secret key used by Flask for session management and CSRF protection. Generate a secure random key for your installation.
- `DATABASE_URI`: The database connection string. Default uses SQLite with a local `posts.db` file.


### Code Implementation

In your `main.py`:
```python
from flask import Flask
from dotenv import load_dotenv
import os

# Load environment variables from .env file
load_dotenv()

app = Flask(__name__)
app.config['SECRET_KEY'] = os.getenv('SECRET_KEY')
app.config['SQLALCHEMY_DATABASE_URI'] = os.getenv('DATABASE_URI')
```

### .gitignore Template

```gitignore
# Environment variables
.env

# Virtual environment
venv/
env/

# Python cache
__pycache__/
*.pyc
*.pyo
*.pyd

# Database
*.db
instance/

# IDE
.vscode/
.idea/
*.swp
*.swo
```

## RESTful Routes

| Method | Route | Description |
|--------|-------|-------------|
| GET | `/` | Display all blog posts |
| GET | `/posts/<post_id>` | Display a specific blog post |
| GET/POST | `/add` | Create a new blog post |
| GET/POST | `/edit-post/<post_id>` | Edit an existing blog post |
| GET | `/delete/<post_id>` | Delete a blog post |
| GET | `/about` | About page |
| GET | `/contact` | Contact page |

## Database Schema

### BlogPost Model

- `id`: Integer (Primary Key)
- `title`: String (250) - Unique, required
- `subtitle`: String (250) - Required
- `date`: String (250) - Required
- `body`: Text - Required
- `author`: String (250) - Required
- `img_url`: String (250) - Required

## Project Structure

```
.
├── main.py                 # Main application file
├── .env                    # Environment variables (not in git)
├── .env.example            # Environment variables template
├── .gitignore              # Git ignore file
├── posts.db               # SQLite database (auto-generated)
├── requirements.txt       # Python dependencies
├── templates/             # HTML templates
│   ├── index.html
│   ├── post.html
│   ├── make-post.html
│   ├── about.html
│   └── contact.html
└── static/               # CSS, JS, and images
```

## Usage

### Creating a New Post
1. Navigate to `/add`
2. Fill in the form with post details
3. Use the rich text editor for the post body
4. Click "Submit Post"

### Editing a Post
1. View a blog post
2. Click the edit button
3. Modify the post details
4. Save changes

### Deleting a Post
1. View a blog post
2. Click the delete button
3. The post will be permanently removed

## Generating a Secret Key

To generate a secure secret key for production:

```python
import secrets
print(secrets.token_hex(16))
```

Or in the terminal:
```bash
python -c "import secrets; print(secrets.token_hex(16))"
```




--- 

<img width="500px" alt="image" src="https://github.com/user-attachments/assets/33c0594d-0047-4881-b19c-0c26dc39e147" />
<img width="500px" alt="image" src="https://github.com/user-attachments/assets/b65467f0-4730-4296-95a6-9c17c131b86b" />





