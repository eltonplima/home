```bash
heroku login
# Run a command inside the app container
heroku run -a APP_NAME python manage.py command
# Continous log like: tail -f
heroku logs -t -a APP_NAME
```
