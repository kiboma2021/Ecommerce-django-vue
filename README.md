# Ecommerce-django-vue

-Install and activate virtual environment
-install django, django-rest-framework, django-cors-headers (for security), djoser(to autenticate users), pillow (to resize images),
stripe(for payments)

- start django project

-add to the apps:
rest_framework
rest_framework.authtoken
djoser
corsheaders

configure corsheaders:

CORS_ALLOWED_ORIGINS = [
    'http://localhost:8080/'
]

Add corsheaders to the middleware above common middleware

    'corsheaders.middleware.CorsMiddleware'

-Include djoser in urls




