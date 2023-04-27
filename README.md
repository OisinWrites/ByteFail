Project set-up
     cmnd:  django-admin startproject 'project name'

    Adding apps for bookings and customers
        cmnd:   django-admin startapp 'app name'
        Register app names under installed_apps in settings.py

    Install allauth, refer to allauth documentation
        cmnd: pip3 install allauth
        Add lines 
                    # `allauth` needs this from django
                    'django.template.context_processors.request',
        under templates in settings.py
        Add lines
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

    cmnd: pip3 freeze > requirements.txt 
    to create a file for installed apps that can be summoned for local environment using cmnd: pip3 install -r requirements.txt

    To copy and paste folders and files from allauth site-packages first determine python version installed using cmnd: python --version In this case python3 3.8
    Create a folder, templates, and subfolder, allauth, from the project level directory
    Then run cmnd: cp -r ../.pip-modules/lib/python3.8/site-packages/allauth/templates/* ./templates/allauth/

Credits
Allauth set-up
https://django-allauth.readthedocs.io/en/latest/installation.html