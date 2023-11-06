# Project README

## Overview

This project deploys a containerized web application using Kubernetes on Google Kubernetes Engine (GKE). The application consists of frontend and backend components, with a MongoDB database for data storage. This README explains the choices made regarding Kubernetes objects, methods for exposing pods to internet traffic, and the use of persistent storage.

## Choice of Kubernetes Objects

### Frontend and Backend Deployments

- I have used Kubernetes Deployments for both the frontend and backend components. 
Deployments provide a scalable way to run replicated applications which ensures high availability and fault tolerance by automatically replacing failed pods.

### StatefulSet for MongoDB

- For the MongoDB database, I have opted for a Kubernetes StatefulSet. StatefulSets are used for stateful applications like databases in my case a MongoDB database, providing stable network identities and persistent storage which ensures that each MongoDB pod has a unique identity and retains its data during restarts.

## Methods for Exposing Pods to Internet Traffic

### LoadBalancer Service

- To expose the frontend application to the internet, I have used a Kubernetes LoadBalancer Service. This type of service provides an external IP address, allowing external traffic to access the frontend pods. The LoadBalancer routes traffic to the available frontend replicas.

### ClusterIP Service

- The backend service is exposed as a Kubernetes ClusterIP Service. ClusterIP services are used for internal communication within the cluster. The backend service can be accessed by other services in the cluster but is not exposed to the internet which adds an extra layer of security.

## Use of Persistent Storage

### MongoDB Data

- For the MongoDB database, I have utilized persistent storage by defining Persistent Volume Claims (PVCs). PVCs are used to request and consume storage resources. These PVCs ensure that data stored by MongoDB is retained even if the MongoDB pod is rescheduled or restarted.

### Frontend and Backend Data

- The frontend and backend applications do not require persistent storage as they are stateless and designed to work with ephemeral storage.

## Deploying the Project

To deploy this project to GKE:

1. Create a GKE cluster using the provided instructions in the setup documentation.

2. Apply the Kubernetes manifests for the frontend and backend using `kubectl apply -f frontend-deployment.yaml` and `kubectl apply -f backend-deployment.yaml`.

3. Apply the Kubernetes StatefulSet manifest for MongoDB using `kubectl apply -f mongodb-statefulset.yaml`.

4. Expose the frontend service to the internet using `kubectl apply -f frontend-service.yaml`.

5. Access the application through the LoadBalancer's external IP address. http//:35.229.165.88:8080

## Additional Notes

- Ensure that your GKE cluster has sufficient resources for the application, and that quotas and resource limits are adjusted as needed.

- Monitor the pods and services using `kubectl get pods` and `kubectl get services` to ensure proper deployment and access and `kubectl describe pod (podname)` to view the logs on each pod incase of an error it will help on debugging

- Refer to the specific documentation for each Kubernetes object for advanced configurations and troubleshooting.

Happy deploying!
