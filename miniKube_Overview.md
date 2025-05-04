## Command to download and install minikube
    winget install Kubernetes.minikube

## Command to start the minikube with hyperV 
    minikube start --driver=hyperv

## Command to set the hyperv as default driver
    minikube config set driver hyperv

## Command to get the IP of the machine where the app is running
    minikube ip

## Command to automatically open the service in default browser using the Minikube IP and the service port
    minikube service webapp-service
