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

###VUE
install vue client
    npm install -g @vue/cli
    vue create nextshop_vue (babel, router, vuex, css prep-processor)

- Install axios
    npm install axios (to communicate with backend)

- Install bulma (Css framework)
    npm install bulma 





