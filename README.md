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

**Flux installation**  
Initial requirements: 
  - github account with access token generated
  - flux command line tool istalled
  
Aplication deployment can be also done using FluxCD tool:  
  1. Start Minikube cluster - `minikube start`
  2. Enable ingress addon - `minikube addons enable ingress`
  3. Confirm that current context is set to minikube cluster - `kubectl config get-contexts`
  4. Bootstrap the toolkit components on the targeted Git provider and minikube cluster - `flux bootstrap github --owner=<username> --repository=<new_repo_name> --branch=main --personal --path=clusters/django`
  5. Clone new created repo
  6. Copy 'apps' and 'infra-common' folders from https://github.com/Digitalpit/demo-django.git repo to your new repo
  7. Take from demo-django\clusters\test folder 3 files ('dev.yaml', 'test.yaml', 'infra-common.yaml') and copy to your new repo to clusters/django folder
  8. Commit all files and check when resourses will be deployed to your cluster

## 12-factor app model

  - I. Codebase - application and images stored in one central repo
  - III. Config - some parameters from config moved from settings.py to configmap and secret
  - V. Build, release, run - there are separate stages building image, configuration and deployment to cluster
  - VII. Port binding - we have pod (with application) as one service, cluster IP i second and ingress is the first one and one service becomes the backing service for another
  - IX. Disposability - application as container starts and stops in seconds
  - X. Dev/prod parity - in containers we have it as manifests are also very similar 

## Local development

Kind would be good solution to help developers to deploy application to local cluster. 
Process can look like below:  
  - developer develops application locally 
  - once he makes commit locally, create image locally
  - kind has the ability to load local images directly into the cluster so developer can deploy new image in local kind cluster without pushing it to repo
  - after application deployed succesfully locally developer can run some basic tests

