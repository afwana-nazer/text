Step 4: Create an App

Inside project folder:

python manage.py startapp myapp

Now register app in:

📂 myproject/settings.py

Add this inside INSTALLED_APPS:

'myapp',
✅ Step 5: Database Setup

By default Django uses SQLite (no need to install separately).

In settings.py you will see:

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}

That’s it ✅ SQLite is ready.

✅ Step 6: Create Model (Table)

Open:

📂 myapp/models.py

Example:

from django.db import models

class Student(models.Model):
    name = models.CharField(max_length=100)
    age = models.IntegerField()

    def __str__(self):
        return self.name
✅ Step 7: Make Migrations (Create Table)
python manage.py makemigrations
python manage.py migrate

Now table is created in database 🎉

✅ Step 8: Create Admin User
python manage.py createsuperuser

Enter username, email, password.

Run server:

python manage.py runserver

Open:

http://127.0.0.1:8000/admin

Login with superuser account.

✅ Step 9: Show Model in Admin

Open myapp/admin.py

from django.contrib import admin
from .models import Student

admin.site.register(Student)

Now refresh admin page → You can add Students 🎉

🔵 If You Want MySQL Instead of SQLite

Install:

pip install mysqlclient

Change DATABASES in settings.py:

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'mydatabase',
        'USER': 'root',
        'PASSWORD': 'yourpassword',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}

Then run:

python manage.py migrate# text
