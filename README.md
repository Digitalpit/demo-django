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

## Application manifest

Simple application manifest is in install/install-app.yaml file

'apps' and 'infra-common' folders contain manifests that can be used do deploy application using FluxCD tool https://fluxcd.io/.

## Installation 

Initial requirements: 
  - clone repo https://github.com/Digitalpit/demo-django.git
  - use existing imgages from https://hub.docker.com/r/pdziedziel/images/tags or create new ones and then change 'image' parameter in the deployment manifest.

**Simple installation**  
Simple installation can be done on Minikube:  
  1. Start Minikube cluster - `minikube start`
  2. Enable ingress addon - `minikube addons enable ingress`
  3. Confirm that current context is set to minikube cluster - `kubectl config get-contexts`
  4. Go to 'install' folder and use kubectl tool to apply manifest to your cluster - `kubectl apply -f install-app.yaml`
  5. Check IP of the ingress and add to your local hosts file mapping ingress IP -> host parameter (django-dev.com)
  6. Access application by http://django-dev.com/polls/ or http://django-dev.com/admin
  7. Create admin application user by loggin to terminal of the pod and run following command in /app folder - `python manage.py createsuperuser`

