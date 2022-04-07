# demo-django

## Image creation 
Dockerfile
```
FROM python:3

ENV PROJECT_ROOT /app
WORKDIR $PROJECT_ROOT
COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt
COPY . .
CMD python manage.py migrate ; python manage.py runserver 0.0.0.0:8000
```
To create image clone repo, go to source_code folder and run 'docker build' and then 'docker push' to push image to your repo.

Ready to use images available at: https://hub.docker.com/r/pdziedziel/images/tags

