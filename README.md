# Backend_Script3_Blogapp_Models
Django migrates with SQLite3 using shell and admin UI platform

![](https://raw.githubusercontent.com/QueenieCplusplus/Backend_Script3_-logapp_Models/main/18%20post2.png)


prepare virtual env =>

    ~$ virtualenv -p /usr/bin/python3 vir_name

    ~$ source vir_name/bin/activate
    
    (vir_name) ~$cd proj_name
    
    (vir_name) proj_name$ cd site_name
    
    (vir_name) site_name$ ls
    
                   sub_site_name/
                   
                   manage.py
                   
                   (sqlite3 waits to be created)
                   
                   (blog app waits to be created)/


top level site cmd =>


    python manage.py runserver

    python manage.py makemigrations

    python manage.py migrate
    
 
 create a blog =>
 
 
    python manage.py startapp kblog
    
    
 create super user =>
 
 
    python3 manage.py createsuperuser
    
    Username (leave blank to use 'katesandroid'): xxxxx
    Email address: xxx@gmail.com
    Password: 
    Password (again): 
    Superuser created successfully.
    (k0219) KatesAndroiddeMacBook-Pro:site0219 katesandroid$ python manage.py runserver
    Watching for file changes with StatReloader
    Performing system checks...

    
    
 db operations =>
 
    python manage.py shell
    
    
    
    >>> from kblog.models import Post
    >>> Post.objects.all()
    >>> 
    >>> 
    <QuerySet []>
    
    
    >>> Post.objects.create(author=user, title='Sample title', text='Test')
    >>> 
    Traceback (most recent call last):
      File "<console>", line 1, in <module>
    NameError: name 'user' is not defined
    >>> Post.objects.create(author='kate chen', title='Sample title', text='Test')
    ValueError: Cannot assign "'kate chen'": "Post.author" must be a "User" instance.
    
    
    >>> from django.contrib.auth.models import User
    >>> User.objects.all()
    <QuerySet []>
    
    
    >>> user = User.objects.get(username='Poupou Chen')
    Traceback (most recent call last):
      File "<console>", line 1, in <module>
      File "/Users/katesandroid/k0219/lib/python3.8/site-packages/django/db/models/manager.py", line 85, in manager_method
        return getattr(self.get_queryset(), name)(*args, **kwargs)
      File "/Users/katesandroid/k0219/lib/python3.8/site-packages/django/db/models/query.py", line 429, in get
        raise self.model.DoesNotExist(
    django.contrib.auth.models.User.DoesNotExist: User matching query does not exist.
    
    
    >>> from django.contrib.auth.models import User
    >>> User.objects.all()
    <QuerySet []>
    
    
    >>> from django.contrib.auth.models import User
    >>> user = User.objects.create_user('Poupou', 'poupou@pattyappier.com', '0123456789')
    >>> user.save()
    >>> 

    >>> from django.contrib.auth.models import User
    >>> User.objects.all()
    <QuerySet [<User: Poupou>]>
    
    
    >>> user = User.objects.get(username='Poupou')
    >>> Post.objects.create(author = user, title = 'Cats Lovely Home', text = 'Test')
    <Post: Cats Lovely Home>
    
    
    >>> Post.objects.all()
    <QuerySet [<Post: Cats Lovely Home>]>
    
    
    >>> post = Post.objects.get(id=1)
    >>> post.publish()
    >>> 
    >>> Post.objects.filter(published_date__isnull=False)
    <QuerySet [<Post: Cats Lovely Home>]>
    >>> exit()


deprecated cmd => https://stackoverflow.com/questions/17392015/error-while-creating-a-model-in-django

create superuser => https://developer.mozilla.org/zh-TW/docs/Learn/Server-side/Django/Admin_site

blog app  & models init => https://carolhsu.gitbooks.io/django-girls-tutorial-traditional-chiness/content/django_start_project/README.html

models tip => https://www.itread01.com/content/1545016715.html

create user => https://docs.djangoproject.com/en/3.1/topics/auth/default/
