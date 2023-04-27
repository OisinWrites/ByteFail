Project set-up
    django-admin startproject 'project name'
Adding apps for bookings and customers
    django-admin startapp 'app name'
    Register app names under installed_apps in settings.py
Install allauth, refer to allauth documentation
    pip3 install allauth
    Add lines 
                # `allauth` needs this from django
                'django.template.context_processors.request',
    under templates in settings.py
                'django.contrib.sites',

                'allauth',
                'allauth.account',
                'allauth.socialaccount',
    under installed_apps in settings.py
    Create section in settings above templates
                AUTHENTICATION_BACKENDS = [
                ...
                # Needed to login by username in Django admin, regardless of `allauth`
                'django.contrib.auth.backends.ModelBackend',

                # `allauth` specific authentication methods, such as login by e-mail
                'allauth.account.auth_backends.AuthenticationBackend',
                ...
                ]
    Under installed apps
                SITE_ID = 1
    In urls.py
                from django.urls import path, include
                from django.conf import settings


                urlpatterns = [
                    path('accounts/', include('allauth.urls')),
                ]


Credits
Allauth set-up
https://django-allauth.readthedocs.io/en/latest/installation.html