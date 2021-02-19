# Backend_Script3_Blogapp_Models
Django migrates with SQLite3 using shell and admin UI platform

![](https://raw.githubusercontent.com/QueenieCplusplus/Backend_Script3_-logapp_Models/main/18%20post2.png)

top level site cmd =>


    python manage.py runserver

    python manage.py makemigrations

    python manage.py migrate
    
 
 create a blog =>
 
 
    python manage.py startapp kblog
    
    
 db operations =>
 
    python manage.py shell
    
    
    
    >>> from kblog.models import Post
    >>> Post.objects.all()
    <QuerySet []>
    >>> Post.objects.create(author=user, title='Sample title', text='Test')
    Traceback (most recent call last):
      File "<console>", line 1, in <module>
    NameError: name 'user' is not defined
    >>> Post.objects.create(author='kate chen', title='Sample title', text='Test')
    Traceback (most recent call last):
      File "<console>", line 1, in <module>
      File "/Users/katesandroid/k0219/lib/python3.8/site-packages/django/db/models/manager.py", line 85, in manager_method
        return getattr(self.get_queryset(), name)(*args, **kwargs)
      File "/Users/katesandroid/k0219/lib/python3.8/site-packages/django/db/models/query.py", line 445, in create
        obj = self.model(**kwargs)
      File "/Users/katesandroid/k0219/lib/python3.8/site-packages/django/db/models/base.py", line 483, in __init__
        _setattr(self, field.name, rel_obj)
      File "/Users/katesandroid/k0219/lib/python3.8/site-packages/django/db/models/fields/related_descriptors.py", line 215, in __set__
        raise ValueError(
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
    >>> user = User.objects.set(username='Kate Chen')
    Traceback (most recent call last):
      File "<console>", line 1, in <module>
    AttributeError: 'UserManager' object has no attribute 'set'
    >>> from django.contrib.auth.models import User
    >>> user = User.objects.create_user('Poupou', 'poupou@pattyappier.com', '0123456789')
    >>> user.save()
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
    >>>  exit()
      File "<console>", line 1
        exit()
        ^
    IndentationError: unexpected indent
    >>> exit()



deprecated cmd => https://stackoverflow.com/questions/17392015/error-while-creating-a-model-in-django

create superuser => https://developer.mozilla.org/zh-TW/docs/Learn/Server-side/Django/Admin_site

blog app  & models init => https://carolhsu.gitbooks.io/django-girls-tutorial-traditional-chiness/content/django_start_project/README.html

models tip => https://www.itread01.com/content/1545016715.html

create user => https://docs.djangoproject.com/en/3.1/topics/auth/default/
