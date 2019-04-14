# flask-microservices-users

This is just me messing around with http://testdriven.io take on microservices. 

It will perhaps impact [CD2](https://github.com/CODESIGN2/) in the future. (It never did)

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
docker-compose exec -it users-service python manage.py recreate_db
docker-compose run --rm users-service python manage.py test

```

### Note

This started out as pretty much copy->paste. Follow the tutorial at http://testdriven.io if you want to learn this stuff. The repo will probably be deleted at some point. 


### Opinion (2 years later)
It's pretty vanilla and I'm not sure I agree with everything the tutorial says to do.

* Having healthchecks and using modern docker-compose and baking source-code into the image is a not awful deployment strategy, but it needs work.

If you were to push the docker-image built to dockerhub, you should capture the SHA of your commit (could correspond to a release or tag) so that you're not reliant on `latest` and can experiment with different versions of micro-services. The easiest command to get started with that is `git rev-parse --verify HEAD`

* SQLAlchemy is a hot mess and should not be used

I currently work at a place that uses SQLAlchemy. It's slow, it makes surprises about behaviour easy and it encourages poor reasoning about systems that I've not seen with parametrized SQL.

