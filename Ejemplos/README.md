# Introducion a Kubernetes

## Crear imagen Docker

```
docker build -t oscarllamas6/hello-golang:latest .
docker run -d -p 8080:8080 oscarllamas6/hello-golang:latest
docker push oscarllamas6/hello-golang:latest
```

## Hacer deploy de objectos Kubernetes
```
kubectl apply -f ./k8s/
kubectl get all
```