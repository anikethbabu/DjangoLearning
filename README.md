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
If you want to force kill the server run
'''
fuser -k 8000/tcp
'''
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

## Database
For creating a database table update the models directory with a table and its fields. Then run the command
```
python manage.py makemigrations
```
After the code has ran you will see a migrations directory pop up with code for the database.

To view the sql that will be ran from this you can run 
```
python manage.py sqlmigrate blog 0001
```
To finish migrations and update the database run.
```
python manage.py migrate
```

To open up python Interactive Console to run queries and edits with the tables. You can run command. 
```
python manage.py shell
```
In the interactive terminal you can work with the django objects.

First you have to run
```
from blog.models import Post
```
```
from django.contrib.auth.models import User
```
After running that you can work with User db objects. Using
```
User.objects.all()
```
You can filter based on a field using the command below.
```
User.objects.filter(username='anikethbabu')
```
You also use first to get the first item in the query.

```
User.objects.first()
```
You can also store it in a variable.
```
user = User.objects.filter(username='anikethbabu').first()
```
After creating the user variable you can look at the attributes of the the user.
```
user.id
user.pk
```
You can also get user based on attributes
```
user = User.objects.get(id=1)
```
To store in post table you can run
```
post_1 = Post(title='Blog 1', content='First Post Content!', author = user)
post_1.save()
```

In django if you register the model to admin you can access all the information in the admin gui and make edits and changes.

## Django Register
In views you can import UserCreationForms for an easy register form from django. You just pass the form variable when rendering the template. Check if the form has post data and if its valid and flash a user creation sucess method. To create a form with extra fields you have to create a forms.py file that inherits from UserCreationForm and add the fields that you want. You can add a an inner class meta in your forms to show specify the model and fields. For good styling on forms and good feedback install crispy forms using
```
pip install django-crispy-forms
```
These after that add it to the settings.py file in the django project specify the template pack. After that you can go into your forms and use 
```
{% load crispy_forms_tags %}
```
```
{{ form|crispy }}
```
For more information visit: https://django-crispy-forms.readthedocs.io/en/latest/