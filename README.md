\# CI/CD Pipeline using Jenkins, Docker \& Kubernetes



\## Project Overview



This project demonstrates an end-to-end CI/CD pipeline for automatically testing, containerizing, and deploying a web application.



The pipeline integrates GitHub, Jenkins, Docker, Docker Hub, and Kubernetes (Minikube) to automate application deployment.



\## Architecture



GitHub → Jenkins → Docker → Docker Hub → Kubernetes (Minikube) → Browser



\## Technologies Used



\- Jenkins

\- Docker

\- Docker Hub

\- Kubernetes

\- Minikube

\- kubectl

\- Git

\- GitHub

\- Nginx

\- HTML



\## Project Structure



```text

jenkins-docker-kubernetes/

│

├── Dockerfile

├── Jenkinsfile

├── deployment.yaml

├── service.yaml

├── index.html

├── screenshots/

└── README.md

**CI/CD Pipeline**

1.Developer pushes application changes to GitHub.

2.Jenkins checks out the latest source code.

3.Jenkins performs an application test.

4.Jenkins builds a Docker image.

5.Jenkins authenticates with Docker Hub.

6.Jenkins pushes the Docker image to Docker Hub.

7.Jenkins deploys the application to Kubernetes.

8.Kubernetes performs a rolling update.

9.Jenkins verifies the deployment.

10.The updated application is accessed through a Kubernetes NodePort service.



**Docker**



The application is containerized using Nginx and Docker.



Docker images are tagged using the Jenkins build number:



nawfel03/my-web-app:<BUILD\_NUMBER>





**Kubernetes**



The application is deployed on a Minikube Kubernetes cluster using:



* Kubernetes Deployment
* 2 replicas
* NodePort Service
* Nginx container



**Jenkins Pipeline Stages**



* Checkout
* Test
* Build Docker Image
* Docker Login
* Push Docker Image
* Deploy to Kubernetes
* Verify Deployment



**Application**



The web application is a simple HTML page served using Nginx.



The CI/CD pipeline was tested by modifying the application and automatically deploying the updated version through Jenkins.



**Screenshots**



Project screenshots are available in the screenshots folder.



**Key Skills**



Jenkins | Docker | Docker Hub | Kubernetes | Minikube | Git | GitHub | CI/CD | Containerization | Kubernetes Deployment

