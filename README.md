## *Django(web-framework for python) Highlights:-*

	a. Fast

	b. Components available

	c. Security

	d. Scalability


## *MVT (Model View Template) ---> equivalent to MVC (Model View Controller)*

### **Installation:-**

	$ python3 -m venv ~/.virtualenvs/djangodev

	$ source ~/.virtualenvs/djangodev/bin/activate
 
 	$ python -m pip install Django

 	$ python -m django --version

 ## *Django Project setup:-*

 	1.$ django-admin startproject <name>

 		Files created:-
 		./ls
 			<name> manage.py

 			<name>/ls
 			 		 __init__.py asgi.py     settings.py urls.py     wsgi.py


 	2. manage.py--> 
 	   wsgi.py--> Deploy your project on the server
 	   urls.py--> Website will have lot of urls, this file handles that
 	   asgi.py--> 

 	3. $ python manage.py runserver

 	4. paste http://127.0.0.1:8000/ on web-browser

 	
 ## *Using Django build Application:-*

 	1. Static vs Dynamic

 		 Static--> everyone sees the same thing
 		 Dynamic--> customer specific

 	2. Making Simple Application Ex. calc

 	 	 $ python manage.py startapp calc

 	 	 	- this creates a basic application with a bunch of files

 	 	 - create urls.py (this is specific to this app so that it only affects this application), 
 	 	   view the file in project for more info

 	 	 - create a function inside views.py & use HttpResponse to reply back to the request

 	 	 - after this, add path of app under urlpatterns to the project's urls.py

 	 	 - also, go to settings.py and add the app name under installed_apps

 	 	 - go to the urls.py of the app created:-

 	 	 		Ex. from . import views

				urlpatterns = [
    			path('', views.home, name='home'),
				]
		- go to the urls.py of the project created;-

				Ex. from django.contrib import admin
					from django.urls import path, include

					urlpatterns = [
    				path('admin/', admin.site.urls),
    				path('',include('portal.urls'))


					]
		 - If you edit the models.py of the app, the changes have to be migrated. Use following commands:-

		 		$ python manage.py makemigrations

		 		$ python manage.py migrate



 	 	 - to avoid static page and make it dynamic we use Templates (DTL--> Django Template Language (jinja format)), 
 	 	   the text is dynamic rest is static ex. bg color, font etc.

 	 	 - create "templates" folder outside your applications under your project

 	 	 - Now, we create a home.html file under templates & write some text with headers

 	 	 - We further need to make changes to the settings.py of the main folder & under templates, 
 	 	   we need to provide the path to the folder templates

 	 	 - After this, we also need to make changes to the views.py of the application and 
 	 	   rather than using HttpResponse we replace it with render and call the home.html page

 	 	 - Most of the pages will have same theme and just the data would be different, 
 	 	   so we create base.html(!-->enter would create a basic layout on base.html)for this purpose

 	3. Get vs Post data

 		  - Until now, we used get and saw that all the data was displayed on the address bar, 
 		  you don't want that for your Username & Password

 		  - Hence, we will use the POST data instead now

 		  - use method='post' in the form action (only this won't suffice, CSRF attack vulnerable) 
 		  + {% csrf_token%} under home.html + change the GET to post under function addition(in this case) in views.py

 		 - So, whenever we post data we use POST and fetch data we use GET


 	4. MVT (Model View Template)

 		 - Layout & Data are two most important things you look for in a webpage

 		 - Now, what if you want a dynamic content ex. amazon history of a user, everyone's different

 		 - We need three--> Data, Layout, Logic (separation of concerns)

 	5. Working on UI

 	         - Download travello colorlib

 	         - Make another app named travello (in this example)

 	         - Copy the urls.py from previous app and change the function (to show if it's working)

 	         - Change the render request to the new page (of new app ex index.html)

 	         - Change the setting in the common urls.py and write in "travello.py" to see change on localhost display

 	         - Set up your static files now (if in index.html you are calling some files, you need them in your project as well)

 	         - Inform Django where to find the static files in settings.py

 	         - change href,style,image,js tc.(inspect and see errors) to ex. "{% static 'styles/bootstrap4/bootstrap.min.css' %}" for each url you see in index.html --> Django understandable 

 	         - Also, add "{% load static %}" to the top 

 	6. ORM (Object Relational Mapper)

 	         - Directly generate tables with classes you create and generate data with objects you create
    

    *Migration*

 	7. Postgres & pgadmin(for UI of postgres)

 	8. Create a new database on pgadmin, go back to setting.py and enter the details in Databases.Now, further connect Django and Postgresql using psycopg2 adapter

 	9. python -m pip install psycopg2 (if you get any error for psycopg2 module, use this command instead)

 	10. After installation, execute-->python manage.py sqlmigrate travello(app name) 0001(name of migration)

 	11. python manage.py migrate

 	12. Re-Migration

 		- Make changes

 		- python manage.py migrate

 	13. Now, by this time our table is created on pgadmin

 	14. Now, for your running server on localhost

 		- 127.0.0.1:8000/admin

 			- This will give you a login username and password (by default provisioned by Django but since, you don't have any, you would create one)

 			- on the command line

 				 $ python manage.py createsuperuser

 	15. Now, 127.0.0.1:8000/admin -->login--> you can now add more users

 	16. Resiter the model in admin.py and it automatically creates a page for you ex. Destination in this case

 	17. Under views.py funtion use --> dests = Destination.objects.all() and this fetches all the data you added on the admin page

 	18. You can see pics are syced to the media-->pics folder as well but it's not yet reflected on the webpage

 	19. In your index.html --> <img src="{{dest.img.url}}" alt=""> . This pics up the images you uploadec

 	20. Created a form for user to register itself on the portal

 	21. Now, the registration has to sync up with the database

 	22. Passing Messages in Django

 	23. Creating Login button & verifying credentials

 	24. Using Bootstrap:-

 	25. Starter Template

 		- https://getbootstrap.com/docs/4.5/getting-started/introduction/

	26. Buttons

 		- https://getbootstrap.com/docs/4.5/components/buttons/
 	27. Create Forms on Django

 		- datepicker (Installation & Bug resolutions)

 			- https://stackoverflow.com/a/35968816/9420870

 			- https://github.com/monim67/django-bootstrap-datepicker-plus

 			- https://stackoverflow.com/a/59266325/9420870

 			- https://django-bootstrap-datepicker-plus.readthedocs.io/en/latest/Usage.html#custom-form-usage

 	28. Django Form Validation (field required or not required to answer)

 		- https://stackoverflow.com/questions/1134667/django-required-field-in-model-form

 	29. Calendar

 	       - Reference:-
 		       - https://www.huiwenteo.com/normal/2018/07/24/django-calendar.html

 		       - https://www.huiwenteo.com/normal/2018/07/29/django-calendar-ii.html



## Common Troubleshooting:-
      1. If python migrate is giving errors, execute both a&b below on your project terminal:-
         a> find . -path "*/migrations/*.p" -not -name "__init_
          _.py" -delete
         b> find . -path "*/migrations/*.pyc"  -delete```

