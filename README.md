# Django ToDo list

This is a todo list web application with basic features of most web apps, i.e., accounts/login, API, and interactive UI. To do this task, you will need:

- CSS | [Skeleton](http://getskeleton.com/)
- JS  | [jQuery](https://jquery.com/)

## Explore

Try it out by installing the requirements (the following commands work only with Python 3.8 and higher, due to Django 4):

```
pip install -r requirements.txt
```

Create a database schema:

```
python manage.py migrate
```

And then start the server (default is http://localhost:8000):

```
python manage.py runserver
```

Now you can browse the [API](http://localhost:8000/api/) or start on the [landing page](http://localhost:8000/).

## Task

Create a kubernetes manifest for a pod which will containa ToDo app container:

1. Fork this repository.
1. Create a `statefulSet.yml` file for `StatefulSet` to manage MySQL.
1. `StatefulSet` requirement:
    1. `StatefulSet` should be deployed in a `mysql` namespace
    1. `StatefulSet` should have 3 replicas
    3. `StatefulSet` is reading sensetive data from a secret:
        1. `MYSQL_ROOT_PASSWORD`
        1. `MYSQL_USER`
        1. `MYSQL_PASSWORD`
    4. `StatefulSet` pods should have a `livenessProbe` and `readinessProbe`
    5. `StatefulSet` pods should have a `requests` and `limits` for `CPU` and `Memory`
    6. MySQL db should be inited from an `init.sql` that should be propagated as a mounted volume in `/docker-entrypoint-initdb.d`
    7. `StatefulSet` should have `volumeClaimTemplates`
    8. `SteatefulSet` should have a headless `Service` to expose db pods
1. Update your application so it could connect to a 0 indexed db pod (mysql-0)
1. Application should read db connecion information from a `Secret`.
1. `README.md` should have commands to apply all components in a right order
1. `README.md` should have instructuions on how to validate the changes
1. Create PR with your changes and attach it for validation on a platform.
