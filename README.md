# Django Notes App on Kubernetes

A simple Kubernetes deployment of a Django Notes application.

This project demonstrates the fundamentals of deploying a containerized application on Kubernetes using core Kubernetes resources.

## Technologies Used

* Kubernetes
* Docker
* Django
* YAML

## Kubernetes Resources

* **Namespace** – Isolates the application within the cluster.
* **Deployment** – Manages the application Pods and ensures the desired number of replicas are running.
* **Service** – Exposes the application using a Kubernetes Service.

## Project Structure

```text
.
├── deployment.yaml
├── service.yaml
├── namespace.yaml
└── README.md
```

## Prerequisites

* Kubernetes cluster (Kind, Minikube, kubeadm, or any Kubernetes environment)
* kubectl

## Deployment

Create the namespace:

```bash
kubectl apply -f namespace.yaml
```

Deploy the application:

```bash
kubectl apply -f deployment.yaml
```

Create the Service:

```bash
kubectl apply -f service.yaml
```

## Verify the Deployment

Check the namespace:

```bash
kubectl get ns
```

Check the Pods:

```bash
kubectl get pods -n notes-app
```

Check the Deployment:

```bash
kubectl get deployments -n notes-app
```

Check the Service:

```bash
kubectl get svc -n notes-app
```

## Accessing the Application

### Using ClusterIP

```bash
kubectl port-forward -n notes-app svc/notes-app-service 8000:8000
```

Then open:

```
http://localhost:8000
```

### Using NodePort

If the Service type is changed to `NodePort`, access the application using:

```
http://<NODE-IP>:<NODE-PORT>
```

For example:

```
http://<NODE-IP>:30080
```

## Features Demonstrated

* Kubernetes Namespace
* Kubernetes Deployment
* Kubernetes Service
* Pod Management
* Label Selectors
* Container Port Configuration

## Learning Outcome

This project demonstrates how Kubernetes Deployments, Services, and Namespaces work together to deploy and expose a containerized Django application.
