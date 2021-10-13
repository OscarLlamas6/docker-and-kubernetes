# Conexion a mongoDB en Kubernetes con Mongo Compass

## Manifiesto YAML

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mongodb-deployment
  labels:
    app: mongodb
spec:
  replicas: 1
  selector:
    matchLabels:
      app: mongodb
  template:
    metadata:
      labels:
        app: mongodb
    spec:
      containers:
      - name: mongodb
        image: mongo:latest
        ports:
          - containerPort: 27017
        volumeMounts:
          - name:  host-volume
            mountPath: "/data/db"
      volumes:
        - name: host-volume
          hostPath:
            path: /mongo/database
---
apiVersion: v1
kind: Service
metadata:
  name: mongodb-service
spec:
  selector:
    app: mongodb
  ports:
    - protocol: TCP
      port: 27017
      targetPort: 27017    
```

## Hacer deploy de lo objetos Kubernetes

```bash
$ kubectl apply -f mongodb-deployment.yaml 
deployment.apps/mongodb-deployment unchanged
service/mongodb-service created

$ kubectl get svc
NAME              TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)     AGE
kubernetes        ClusterIP   10.96.0.1       <none>        443/TCP     8d
mongodb-service   ClusterIP   10.106.245.46   <none>        27017/TCP   100s

$ kubectl describe service mongodb-service 
Name:              mongodb-service
Namespace:         default
Labels:            <none>
Annotations:       Selector:  app=mongodb
Type:              ClusterIP
IP:                10.106.245.46
Port:              <unset>  27017/TCP
TargetPort:        27017/TCP
Endpoints:         172.18.0.8:27017
Session Affinity:  None
Events:            <none>

$ kubectl get pod -o wide
NAME                                 READY   STATUS    RESTARTS   AGE   IP           NODE       NOMINATED NODE   READINESS GATES
mongodb-deployment-8b456d6bd-h8phm   1/1     Running   0          86m   172.18.0.8   minikube   <none>           <none>

$ kubectl get all 
pod/mongodb-deployment-8b456d6bd-h8phm   1/1     Running   0          88m
service/mongodb-service   ClusterIP   10.106.245.46   <none>        27017/TCP   10m
deployment.apps/mongodb-deployment   1/1     1            1           88m
replicaset.apps/mongodb-deployment-8b456d6bd   1         1         1       88m

# find mongo pod name
$ kubectl get pods
$ kubectl expose pod <<pod name>> --type=NodePort

# find new mongo service  

$ kubectl get services

```

## La cadena de conexion para mongo Compass seria:

```bash
mongodb://localhost:<NodePortIP>/?readPreference=primary&appname=MongoDB%20Compass&directConnection=true&ssl=false
```