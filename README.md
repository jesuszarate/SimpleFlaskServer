# SimpleFlaskServer

This application uses python 3, you can find download the installer from the official website <https://www.python.org/downloads/>


## **How to get started**

### Creating environment and activating it

```bash
$ python3 -m venv flask-app
$ source flask-app/bin/activate
```

### Installing requirements

```bash
$ pip install -r requirements.txt
```

### Setting Flask app environment variable

Before we run the application we must tell Flask how to import it

```bash
$ export FLASK_APP=SimpleFlaskServer.py
```

### How to run it

```bash
$ flask run
```

### The app will be served at:

http://127.0.0.1:5000/


</br>

# Migrations

### How to migrate

```bash
$ flask db migrate # Does not make changes to database, it just creates the migration script
$ flask db upgrade # Applies the changes to the database
```

### Creating Post table example:

```bash
$ flask db migrate -m "posts table"
$ flask db upgrade
```

</br>

# Interacting with database using python

First run a python interactive session

```bash
$ python
```

### Before starting run
```python
>>> from app import db
>>> from app.models import User, Post
```

### Adding a new user

```python
>>> u = User(username='john', email='john@gmail.com')
>>> db.session.add(u)
>>> db.session.commit() 
```

# Getting all users

```python
>>> users = User.query.all()
```

# Get all posts for a user

```python
>>> posts = u.posts.all()
>>> posts
```

# get all users in reverse alphabetical order
```
>>> User.query.order_by(User.username.desc()).all()
[<User susan>, <User john>]
```

</br>

# API


## Followers/followed
```
http GET http://localhost:5000/api/users/1/followers
http GET http://localhost:5000/api/users/1/followed
```

## Create a user
```
http POST http://localhost:5000/api/users username=alice password=dog email=alice@example.com "about_me=Hello, my name is Alice!"
```

## Edit User

```
http PUT http://localhost:5000/api/users/2 "about_me=Hi, I am Choochoo"
```

## Authenticate

```
http --auth <username>:<password> POST http://localhost:5000/api/tokens
```

## Get user

```
http GET http://localhost:5000/api/users/1 "Authorization:Bearer pC1Nu9wwyNt8VCj1trWilFdFI276AcbS"
```

## Delete token

```
http DELETE http://localhost:5000/api/tokens Authorization:"Bearer pC1Nu9wwyNt8VCj1trWilFdFI276AcbS"
```
