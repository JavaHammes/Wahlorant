# Whalorant

kubectl delete all --all
kubectl delete ingress --all
kubectl delete secret --all
kubectl delete pvc --all

minikube stop
minikube start
minikube addons enable ingress

skaffold dev --profile=dev

minikube tunnel

kubectl get svc
kubectl get pods
kubectl get ingress


# Navigate to your backend directory
cd backend
docker build -t backend:latest .

# Navigate to your frontend directory
cd ../frontend
docker build -t frontend:latest .


kubectl rollout restart deployment/backend
kubectl rollout restart deployment/frontend