# DjangoLearning

## Set up Python Virtual Env and Install Django
Create a python virtual environment for this project.
```
 python3 -m venv django_env
 ```
Ensure that you are in parent directory of django_env.  Activite python virtual environment that was created earlier.
```
source django_env/bin/activate
```

Intall django library using pip
```
pip install django 
```

Verify the django installation
```
python -m django --version 
```


## Initial project setup
Check out list of subcommands by running
```
django-admin
````


Create a initial project using django command line
```
django-admin startproject django_project
```

Check out the list of file djnago generates under django_project.


Launch the server using following command.  Visit the URL specified using a browser
```
python manage.py runserver
```

Visit http://127.0.0.1:8000/admin to check out the admin screen.

Create an app called blog in the django project folder using command.

```
python manage.py startapp blog
```
## Design

Then updated the views file with a home view and imported http response from django.http

In the blog directory a urls.py needs to be created to connect the views. When you visit the website django maps the users url to urls.py in django_project folder. In the urlpatterns string you can add path('blog/', include('blog.urls')) where 'blog/' maps to webaddress/blog and include blog.urls.

Connected .html files and made them run on blog urls on the django website. This was done using the django render command which will render an html template and return it when the right url is visited. You can pass data to a template using render and in the html you can use the variable data through jinja2 templating.

Added boostrap and used template inheritance. Also created a static folder and used {% load static %} to use it in base.html file. 


## Django Admin
To make django admin work first have to create the initial database. Run commands.
```
python manage.py makemigrations
```
```
python manage.py migrate
```
After this you can create a user an admin user with the command. 
```
python manage.py createsuperuser
```
After all that is created you can log onto admin after running the django site and going to the /admin view. There you can add users and privileges and update and change things.