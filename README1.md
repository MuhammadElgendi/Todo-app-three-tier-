# Todo-app-three-tier

## Run Locally

Clone the project

```bash
  Git clone https://github.com/MuhammadElgendi/Todo-app-three-tier-.git
```



Install dependencies

```bash
  npm install
```

Start the server

```bash
  npm run start
```

## Set up the App using the Docker Compose file 
### The docker-compose file will create 3 environments 
- Frontend: has the web tier
- backend: has the API tier 
- mongo: has the database tier based on MongoDB
### To set-up the environments and run the app 
## Make sure that you are in the main dir that contains the docker-compose file  
or access it by running
```bash
cd Todo-app-three-tier
```
## use compose up
```bash
Docker-compose up --build 
```



#### the output
![Screenshot from 2023-02-18 23-46-54](https://github.com/MuhammadElgendi/Todo-app-three-tier-/blob/master/images/Screenshot%20from%202024-06-01%2023-12-38.png?raw=true)
#### Now u can access the app via localhost or by your network from the below provided links  
![Screenshot from 2023-02-18 23-46-54](https://github.com/MuhammadElgendi/Todo-app-three-tier-/blob/master/images/Screenshot%20from%202024-06-01%2023-15-21.png?raw=true)

# the app on the browser
![Screenshot from 2023-02-18 23-46-54](https://github.com/MuhammadElgendi/Todo-app-three-tier-/blob/master/images/Screenshot%20from%202024-06-01%2023-00-17.png?raw=true)


 


#
#
#
# Deploy and set-up the app on minikube cluster 

## cd the k8s dir   
```bash
cd k8s
```

## create a namespace for the app firstly to be isolated from your environment 

```bash
kubectl apply -f namespace.yaml
```
## use the created namespace 
```
kubectl config set-context --current --namespace=my-app
```
## deploy the app on the new namespace
```bash
kubectl apply -f .
```

## check the deployments and services has been deployed successfully 
```bash
kubectl get all -o wide 
```
###  The output must be like 
![Screenshot from 2023-02-18 23-46-54](https://github.com/MuhammadElgendi/Todo-app-three-tier-/blob/master/images/Screenshot%20from%202024-06-01%2023-45-16.png?raw=true)

## access the frontend(web) service
```bash
minikube service my-service --url
```

## The output 
![Screenshot from 2023-02-18 23-46-54](https://github.com/MuhammadElgendi/Todo-app-three-tier-/blob/master/images/Screenshot%20from%202024-06-01%2023-59-37.png?raw=true)


