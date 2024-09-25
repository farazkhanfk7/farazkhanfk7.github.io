+++ 
draft = false
date = 2021-04-05T14:21:51+05:30
title = "Using Signals in Django framework. How do they work ?"
description = ""
slug = "using-signals-in-django-framework"
authors = ["Hasan Faraz Khan"]
tags = ["django","backend"]
categories = []
externalLink = ""
series = []
+++

![captionless image](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*MDmm95oaDAFgbDkjptJALw.jpeg)

The Django Signals can be used to get notified when certain events occur. They can also be used for database logging. Let’s say you want to perform some logic every time a given model instance is updated, but there are several places in your codebase that this model can be updated. You can do that using **signals**, hooking some pieces of code to be executed every time this specific model’s save method is triggered.

In this piece, we’ll look at how we can use Django’s in-built signals, how they work, and how we can create custom signals.

In Django, there are signals for Models, Views, and even authorization. **pre_save** and **post_save** are the most common signals that are used to trigger events every time a model instance is updated. Let’s say we want to create a user’s profile every time a user is registered and a new entry is made in Django’s inbuilt **User** model. This can easily be done using signals.

Consider this as my model for the profile of a user.

```python
>>models.py
class Profile(models.Model):
    user = models.OneToOneField(User,on_delete=models.CASCADE)
    first_name = models.CharField(max_length=20)
    last_name = models.CharField(max_length=20,blank=True)
    profile_pic = models.ImageField(upload_to='pics',default='x')

    def __str__(self):
        return f"{self.first_name} {self.last_name}"
```

There are two key elements in the signals: the _senders_ and the _receivers_. As the name suggests, the _sender_ is the one responsible to dispatch a signal, and the _receiver_ is the one who will receive this signal and then do something. The first thing to do — I created a function that will take an instance of our sender class which in this case is the User model. This function will create the profile for a new user.

```python
def create_profile(sender,instance,created,**kwargs):
    if created:
      Profile.objects.create(user=instance)
      print('Profile Created !')
```

Now, all that left is to connect this function with our signal, so that it is executed every time. This can be done using `post_save.connect()` method. This will take two arguments, first-a function, second-a sender i.e **User** model.

```
from django.db.models.signals import post_savepost_save.connect(create_profile, sender=User)
```

This can also be used with a decorator. `receiver` decorator can be used to connect to a signal and it works quite the same.

```python
def receiver(notification):
   def _wrapper(func):
      if isinstance(signal, (list, tuple)):
         for s in signal:
             s.connect(func, **kwargs)
      else:
         signal.connect(func, **kwargs)
      return func
   return _wrapper
```

This is the code inside receiver decorator.

```python
>>signals.py
from django.dispatch import receiver@receiver(post_save, sender=User)
def update_profile(sender,instance,created,**kwargs):
    if created == False:
       instance.profile.save()
       print("Profile Updated!)
```

The next question— How to use it in our application?

To make it work, the signal needs to be imported in the configuration class inside the _apps.py_ file, also the app should be added to the INSTALLED_APPS list in _settings.py_. Here ‘core’ was the name of my app.

```python
>> apps.py
class CoreConfig(AppConfig):
    name = 'core'
    def ready(self):
       import core.signals
```

Some other useful in-built signals are :

*   django.db.models.signals.**pre_init**: `function(sender,*args,**kwargs)`
*   django.db.models.signals.**post_init**: `function(sender,instance)`
*   django.db.models.signals.**post_delete**: `function(sender,instance,using)`

Find more at : [_Django documentation_](https://docs.djangoproject.com/en/3.1/topics/signals/)

Creating custom signals
=======================

All signals in django, are instance of `django.dispatch.Signal` . We can use it to create custom signals and this time we won’t have to worry about the parameters in the receiver function like sender, instance or created. Now, we can use a single parameter `providing_args` to provide a list of arguments to the receiver.

There are two methods to send signals in Django :

*   send() : This can take multiple argument, the first one is the sender. Rest depends on the list of arguments passed in Signal.
*   send_robust() : This is very similar to send() except it can be used to catch any exception raised by receiver function.

```python
from django.dispatch import Signalnotification = Signal(providing_args=['email','username']@receiver(notification)
def show_notification(sender,**kwargs):
   print(f"Sender is {sender}")
   print(f"Hi,{kwargs['username']} your email is {kwargs['email']}")
   print("Notified")
```

We can trigger this signal from any route.

```python
def register(request):
  notification.send(sender=User,email="xyz@mail.com",username="xyz")
  return HttpResponse("Sent")
```

This was a quick overview of both in-built and custom signals. You can find more about them on official documentation of Django. Happy Coding !