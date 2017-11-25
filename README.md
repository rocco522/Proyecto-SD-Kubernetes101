# kubernetes-101
Proyecto de Sistemas Distribuidos para construir y desplegar una app sencilla de Python en Kubernetes. 

## Acerca de Kubernetes

Kubernetes coordina un cluster de computadores de alta disponibilidad que se conecta como una única unidad para trabajar. Las abstracciones en Kubernetes permite desplegar aplicaciones contenidas en un cluster sin necesidad de atarlas a una máquina individual.

Las aplicaciones contenidas son más flexibles y poseen mayor disponibilidad que otros modelos de despliegue en los cuales las aplicaciones se encuentran directamente instaladas en máquinas específicas como paquetes altamente integrados al host.
Kubernetes automatiza la distribución y la programación de los contenedores de las aplicaciones a lo largo del cluster de forma eficiente. Un cluster Kubernetes está compuesto por dos tipos de recursos, los cuales son mostrados en la Figura 1:

<img src="https://d33wubrfki0l68.cloudfront.net/99d9808dcbf2880a996ed50d308a186b5900cec9/40b94/docs/tutorials/kubernetes-basics/public/images/module_01_cluster.svg">

En windows se prepara el ambiente de kubernetes instalando kubectl. 




## Build a Docker image from existing Python source code and push it to Docker Hub. Replace DOCKER_HUB_USER with your Docker Hub username.
```
cd Docker
docker build -t <DOCKER_HUB_USER>/web .
docker push <DOCKER_HUB_USER>/web
```

## Launch the app with Docker Compose
```
docker-compose up -d 
```

## Test the app
```
curl localhost:5000
```

## Deploy the app to Kubernetes
```
cd ../Kubernetes
kubectl create -f db-pod.yml
kubectl create -f db-svc.yml
kubectl create -f web-pod.yml
kubectl create -f web-svc.yml
kubectl create -f web-rc.yml
```

## Check that the Pods and Services are created
```
kubectl get pods
kubectl get svc
```

## Get the NodePort for the web Service. Make a note of the port.
```
kubectl describe svc web
```

## Test the app by accessing the NodePort of one of the nodes.

```
kubectl get nodes
curl <NODE_IP>:<NODEPORT>
```









# Proyecto-SD-Kubernetes101
