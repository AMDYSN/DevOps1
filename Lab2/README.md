#DevOps Kubernetes exercise 2

steps:
1 - minikube start
2 - create flask application to be deployed as app.py
3 - create dockerfile for app.py
4 - build docker image using minikube docker daemon
  - minikube docker-env displays the variables that would be set if build command is run
  - use eval $(minikube docker-env) to configure Docker CLI to use the minikube Docker daemon
  - finally -> docker build -t flask-app . 
5 - Create a YAML file for the kubernetes deployment -> flask-deployment.yaml
6 - Deploy the application -> minikube kubectl -- apply -f flask-deployment.yaml
7 - Check deployment status and number of replicas -> minikube kubectl get deployments
8 - Verify pods created by the deployment -> minikube kubectl get pods -l app=flask-app
9 - Get the description of the deployment (detailed info) -> minikube kubectl -- describe deployment flask-app
10 - View Deployment logs -> kubectl logs flask-app--b8cd75b6f-tpdpr (replace with actual identifier)
11 - check services -> minikube kubectl -- get services
12 - Try accessing app flask service on the specified port (15000) -> curl https://127.0.0.1:15000
13 - After previous step fails, update flask-deployment.yaml with a service section to access the specified port
   - Apply the changes made to the file -> minikube kubectl -- apply -f flask-deployment.yaml
14 - run -> minikube service flask-app-service --url to get the url to access the app and verify that the deployment works as intended

 
