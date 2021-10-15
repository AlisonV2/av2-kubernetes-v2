# Alison Vandromme - Ynov M1 Docker Elective
Kubernetes - V2

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

### 


