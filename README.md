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

##Include font awesome plugin in index.html

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.2/css/all.min.css">

### SET UP BASE TEMPLATE

### CREATE DJANGO APP AND MODELS FOR PRODUCTS
django-admin startapp product

### SERIALIZERS AND VIEWS FOR THE PRODUCT

### CREATE SIMPLE FRONT PAGE

### VIEW A PRODUCT
    - Create viewset in django
    - create vue page for showing product
    - Add link to detail page























