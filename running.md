kubectl create deployment synergychat-web --image=docker.io/bootdotdev/synergychat-web:latest

minikube start --extra-config "apiserver.cors-allowed-origins=["http://boot.dev"]"

kubectl get pods

kubectl port-forward PODNAME 8080:8080

kubectl edit deployment synergychat-web
