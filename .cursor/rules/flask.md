# Flask Rules for Junior Developers

## 1. Always Use Virtual Environments
- **NEVER** install packages globally on your system
- Always create and activate a virtual environment before starting any Flask project
- Use `python -m venv venv` to create, then `venv\Scripts\activate` (Windows) or `source venv/bin/activate` (Mac/Linux)
- Keep your `requirements.txt` file updated with `pip freeze > requirements.txt`
- This prevents dependency conflicts and ensures consistent environments across different machines

## 2. Follow the Flask Application Factory Pattern
- **NEVER** create your Flask app instance at the module level
- Use the application factory pattern with `create_app()` function
- This allows for better testing, configuration management, and scalability
- Example structure:
```python
def create_app(config_name='development'):
    app = Flask(__name__)
    app.config.from_object(config[config_name])
    # Initialize extensions here
    return app
```

## 3. Never Hardcode Sensitive Information
- **NEVER** put API keys, database passwords, or secrets directly in your code
- Use environment variables with `os.environ.get()` or Flask's `app.config.from_envvar()`
- Create a `.env` file for local development (and add it to `.gitignore`)
- Use Flask's built-in configuration classes for different environments (development, production, testing)
- Example: `app.config['SECRET_KEY'] = os.environ.get('SECRET_KEY') or 'dev-key'`
