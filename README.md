# Whalorant – Development Setup & Commands

## Access the Application
- Frontend: http://app.wahlorant.localhost
- Backend: http://api.wahlorant.localhost

## Cleanup Kubernetes Resources
kubectl delete all --all
kubectl delete ingress --all
kubectl delete secret --all
kubectl delete pvc --all

## Restart Minikube and Enable Ingress
minikube stop
minikube start
minikube addons enable ingress

## Start Development with Skaffold
skaffold dev --profile=dev

## Enable Network Tunneling
minikube tunnel

## Check Kubernetes Resources
kubectl get svc
kubectl get pods
kubectl get ingress

## Build Docker Images Locally
cd backend
docker build -t backend:latest .

cd ../frontend
docker build -t frontend:latest .

## Restart Deployments
kubectl rollout restart deployment/backend
kubectl rollout restart deployment/frontend
