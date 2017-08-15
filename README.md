# flask-microservices-users

This is just me messing around with http://testdriven.io take on microservices. 

It will perhaps impact [CD2](https://github.com/CODESIGN2/) in the future.

# Notes

* hard-bound to SQLAlchemy
* User Model is actually CRUD wrapper repo, not a Model
* Interesting take on application knowing if it's in test, development or production
* docker-compose needs upgrading from xenial stock to follow
    * [docker install](https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/#install-using-the-repository)
    * [docker-compose install](https://docs.docker.com/compose/install/#install-compose-on-linux-systems)
* live volume mount rather than baking application code into image (less unique containers needed)

### Cloning & use

```
git clone git@github.com:Lewiscowles1986/flask-microservices-users.git
docker-compose up -d --build

# Rebuild DB command and test command
docker-compose run users-service python manage.py recreate_db
docker-compose run users-service python manage.py test

```

### Note

This is pretty much copy->pasta, follow the tutorial at http://testdriven.io if you want to learn this stuff. The repo will probably be deleted at some point.

