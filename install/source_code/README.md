# Django Polls App For DevOps Candidates

This is the Django 2.2 tutorial polls app, taken straight from the Django project's official website.

## DevOps Candidates

This app will be used as a base for work that we'll discuss and evaluate during your technical interview. We have a few different tasks based on the level of position you are applying for.

### Junior DevOps Engineer

We ask that you do the following before the interview:

1. Fork this repo
1. Dockerize this app for deployment to kubernetes
1. Write an example set of manifests to deploy this app to Kubernetes
1. Write some brief documentation on how we might launch this app in KIND or Minikube using your manifests

### DevOps Engineer

Do the steps from the junior role, but additionally:

1. Find and fix at least one thing in code does not conform to the [12-factor app model](https://12factor.net/)
1. Create a list of any questions that you would have for the engineering team

### Senior DevOps Engineer

Do the steps above for Junior and Midlevel DevOps Engineers, but additionally:

1. Create or design and describe a local development process for this application
1. Create a basic architecture diagram or description of how you would optimally deploy this application in AWS and Kubernetes. If not enough information or time for this, make sure you have the relevant questions ready for the engineering team to clarify the architecture.

## Goals

Our goals in reviewing this excercise with you are as follows:

1. Evaluate your ability to understand and write basic application code
1. Evaluate your ability to understand and help build a good developer experience
1. Show knowledge of both development and production concerns surrounding microservices and containerized applications
1. Show a basic understanding of Kubernetes resources and declarative infrastructure
1. Show knowledge of what questions and concerns to raise to a product development team or your own teammates in developing and releasing a service
1. See how you would work with us as a team in a normal task-based scenario.

## Deliverables

While all candidates have some different goals, we expect to see the following items completed before our interview:

1. A link to your forked repository that you'd like us to review
1. Documentation in the Git repository on how to run the application for local development
1. A production-ready Dockerfile we could build and deploy to a Kubernetes cluster using the manifests provided
1. For midlevel and senior roles, if you have not emailed us any questions while working on the project, those should be included in a file in the PR.

If you'd like to do so and have time, we'd love to see any of the following:

1. If you choose to need resources outside of Kubernetes, a snippet of Terraform code that describes the resource(s)
1. Create an endpoint in the app that does something of your choosing to demonstrate basic python abilities and ability
to quickly understand a small piece of a web framework. Perhaps it can show the current time, or something similar.

## What to expect

While working on this challenge, you are welcome to email us for any clarification or requirement questions you have. Our recruiter
will let you know who to talk to during this process if you have any questions.

During the interview we will review your work, go through the PR as we would any code review, and discuss
the decisions you made and fixes you chose to implement, as well as any additional concerns you have. Be prepared to also discuss
CI/CD for the app, though we do not expect you to build anything for this.

*We only expect you to spend a couple of hours on this.* You're welcome to do as much as you'd like to do,
but it's not our intention to take up days of your time. If there are things you don't have the time to fix,
please be prepared to talk us through them at the interview. We want you to showcase that you have the knowledge and skills
to help product development teams build, containerize, deploy, and release their apps in the cloud.
