# Django-docker boilerplate

### Install Windows

Run following line to create ```composeexample``` project

```
docker-compose run web django-admin.py startproject composeexample .
```

Change database connection from sqlite to postgres updating the following in ```composeexample/settings.py``` file

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'postgres',
        'USER': 'postgres',
        'HOST': 'db',
        'PORT': 5432,
    }
}
```

Run the ```docker-compose up``` command from the top level directory for your project.

### Usage

Navigate to ```http://localhost:8000``` if you're using Docker for Windows.

If you're using Docker Toolbox, type the command below to find out the virtual host IP address:

```
docker-machine ip default
```

And navigate to the IP address discovered above, for instance: ```http://192.168.99.101:8000```

### Access PostgreSQL Database

To access the database run the following command:

```
docker run -it --rm --link esdjango_db_1:db --net esdjango_default postgres psql -h db -U postgres
```

### Notes

In certain platforms (Windows 10) you might need to edit ```ALLOWED_HOSTS``` inside ```settings.py```. In development enviroment you can set the value to:

```
ALLOWED_HOSTS = ['*']
```

### More Info

https://docs.docker.com/compose/django/
