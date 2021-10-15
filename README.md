# Alison Vandromme - Ynov M1 Docker Elective
Kubernetes - V2

## Stack 

<img src="https://img.shields.io/badge/kubernetes-326ce5.svg?&style=for-the-badge&logo=kubernetes&logoColor=white"/> <img src="https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white" /> <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" /> <img src="https://img.shields.io/badge/Express.js-000000?style=for-the-badge&logo=express&logoColor=white" /> <img src="https://img.shields.io/badge/JavaScript-323330?style=for-the-badge&logo=javascript&logoColor=F7DF1E" /> <img src="https://img.shields.io/badge/npm-CB3837?style=for-the-badge&logo=npm&logoColor=white" />

## Method used

### Step 1: Node Sample App Creation

- Created app.js with Node and Express
- Created a /error route to make the app crash on path match
- Tested the app in browser

### Step 2: Node App Dockerization

- Wrote Dockerfile
- Created docker-compose
- Tested the app (port 80/story)

### Step 3: Push docker image to DockerHub

- Created repo on DockerHub
- Added tag to local image
- Pushed image to DockerHub

```sh
docker build -t alisonv2/kub-v2 .
docker push alisonv2/kub-v2
```

### Step 4: Kub Files Creation

- Created deployment.yaml
- Created service.yaml
- Applied them to Minikube
- Checked if the deployment has correctly been applied
- Checked if the service has correctly been applied

```sh
minikube start
kubectl apply -f service.yaml -f deployment.yaml
kubectl get deployments
kubectl get services
```

- Exposed service with Minikube
- Used the exposed URL to test the application in Postman

```sh
minikube service story-service
```

In Postman : GET and POST requests to {minikube-url}/story 

### Step 5: Persistent Volumes Claim

- Defined a persistent volume
- Created a persistent volume claim
- Checked storage class
- Applied PV and PVC files
- Reapplied deployment
- Checked if PVs and PVCs have been correctly applied

```sh
kubectl get sc
kubectl apply -f host-pv.yaml
kubectl apply -f host-pvc.yaml
kubectl apply -f deployment.yaml
kubectl get pv
kubectl get pvc
```

Why PV?
- To have the volumes totally detached and independants from the Nodes and Pods
- For better reusability in case of a complex application with multiple Nodes and Pods
- To be able to add the CSI type for deployment

Notes : 
- hostPath will only work in local environment as it doesn't work on multiple-nodes environments
- Decided to go with multiple config files instead of one big yaml file for better clarity, as the app will get bigger

### Step 6: Environment Variables & ConfigMap

- Changed app.js to use env variable
- Rebuilt the image
- Pushed the image to DockerHub

```sh
docker build -t alisonv2/kub-v2:2 .
docker push alisonv2/kub-v2:2
```
- Created environment.yaml 
- Applied environment file
- Added env in deployment.yaml
- Reapplied deployment

```sh
kubectl apply -f environment.yaml
kubectl get configmaps
kubectl apply -f deployment.yaml
```

### More on V3 :)