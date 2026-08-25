#DevOps 
Kubernetes exercise

curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube

minikube start

minikube kubectl -- run hello-k8s --image=nginx --port=80

minikube kubectl -- get pods -A

minikube kubectl -- expose pod hello-k8s --type=NodePort --port=80

minikube service hello-k8s
