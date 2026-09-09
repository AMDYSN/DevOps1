#DevOps Kubernetes exercise 2

steps:
- minikube start
- create flask application to be deployed as app.py
- create dockerfile for app.py
- build docker image using minikube docker daemon
  * minikube docker-env displays the variables that would be set if build command is run
  * use eval $(minikube docker-env) to configure Docker CLI to use the minikube Docker daemon
  * finally -> docker build -t flask-app . 
- Create a YAML file for the kubernetes deployment -> flask-deployment.yaml
- Deploy the application -> minikube kubectl -- apply -f flask-deployment.yaml
- Check deployment status and number of replicas -> minikube kubectl get deployments
- Verify pods created by the deployment -> minikube kubectl get pods -l app=flask-app
- Get the description of the deployment (detailed info) -> minikube kubectl -- describe deployment flask-app
- View Deployment logs -> kubectl logs flask-app--b8cd75b6f-tpdpr (replace with actual identifier)
- check services -> minikube kubectl -- get services
- Try accessing app flask service on the specified port (15000) -> curl https://127.0.0.1:15000
- After previous step fails, update flask-deployment.yaml with a service section to access the specified port
   * Apply the changes made to the file -> minikube kubectl -- apply -f flask-deployment.yaml
- run -> minikube service flask-app-service --url to get the url to access the app and verify that the deployment works as intended

 
