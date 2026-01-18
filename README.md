# Software Portal

A web-based software distribution portal built with Python Flask. Allows administrators to manage categories and upload software, while clients can browse and download software either individually or by category.

## Features

### Admin Features
- Create, edit, and delete software categories
- Upload software files to specific categories
- Edit software details (name, version, description)
- View download statistics
- Dashboard with overview statistics

### Client Features
- Browse software by categories
- Download individual software files
- Download entire category as ZIP file
- Search functionality
- View download counts and software details

## Installation

### Prerequisites
- Python 3.8 or higher
- pip (Python package manager)

### Setup Instructions

1. Navigate to the project directory:
```bash
cd software_portal
```

2. Create a virtual environment (recommended):
```bash
python -m venv venv

# On Windows
venv\Scripts\activate

# On Linux/Mac
source venv/bin/activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Run the application:
```bash
python app.py
```

5. Open your browser and navigate to:
```
http://localhost:5000
```

## Default Credentials

### Admin Account
- Username: `admin`
- Password: `admin123`

### Client Account
- Username: `client`
- Password: `client123`

**Important:** Change these default passwords in production!

## Project Structure

```
software_portal/
├── app.py                  # Main application file
├── models.py               # Database models
├── requirements.txt        # Python dependencies
├── uploads/                # Uploaded software files
├── static/
│   └── css/
│       └── style.css       # Custom CSS
├── templates/
│   ├── base.html           # Base template
│   ├── login.html          # Login page
│   ├── admin/              # Admin templates
│   │   ├── dashboard.html
│   │   ├── add_category.html
│   │   ├── edit_category.html
│   │   ├── add_software.html
│   │   ├── edit_software.html
│   │   └── list_software.html
│   └── client/             # Client templates
│       ├── index.html
│       ├── category.html
│       └── search.html
└── software_portal.db      # SQLite database (created automatically)
```

## Configuration

Edit `app.py` to customize:

- `SECRET_KEY`: Change for production security
- `UPLOAD_FOLDER`: Change upload directory location
- `MAX_CONTENT_LENGTH`: Adjust maximum file upload size
- `ALLOWED_EXTENSIONS`: Add/remove allowed file types

## Allowed File Types

By default, the following file types are allowed:
- exe, msi, zip, rar, iso, dmg, deb, rpm, apk, tar, gz, 7z

## Database

The application uses SQLite by default. The database file `software_portal.db` is created automatically on first run.

### Database Tables
- **User**: Stores user accounts (admin and client)
- **Category**: Stores software categories
- **Software**: Stores software information and file paths

## Production Deployment

For production deployment:

1. Change the SECRET_KEY in app.py
2. Set `debug=False` in app.run()
3. Use a production WSGI server (e.g., Gunicorn):
```bash
pip install gunicorn
gunicorn -w 4 -b 0.0.0.0:5000 app:app
```

4. Consider using PostgreSQL or MySQL instead of SQLite
5. Set up proper file permissions for uploads directory
6. Implement SSL/TLS (HTTPS)
7. Set up proper backup for database and uploads

## Docker Deployment (Optional)

Create a `Dockerfile`:
```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
RUN mkdir -p uploads
EXPOSE 5000
CMD ["gunicorn", "-w", "4", "-b", "0.0.0.0:5000", "app:app"]
```

Build and run:
```bash
docker build -t software-portal .
docker run -p 5000:5000 -v $(pwd)/uploads:/app/uploads software-portal
```

## Troubleshooting

### Port already in use
Change the port in app.py:
```python
app.run(debug=True, host='0.0.0.0', port=8080)
```

### File upload fails
- Check upload folder permissions
- Verify MAX_CONTENT_LENGTH setting
- Check disk space

### Database errors
Delete `software_portal.db` and restart the application to recreate the database.

## License

This project is provided as-is for educational and commercial use.

## Support

For issues or questions, please refer to the Flask documentation:
https://flask.palletsprojects.com/
