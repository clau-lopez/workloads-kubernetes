# deployments-kubernetes

## Creating an nginx deployment 

1. Connect to cluster
```
gcloud container clusters  get-credentials {CLUSTER_NAME} --region={REGION_NAME}
```

2. Create a Deployment based on the YAML file: https://github.com/colopezfuentes/deployments-kubernetes/blob/main/application/deployment.yaml

```
kubectl apply -f https://github.com/colopezfuentes/deployments-kubernetes/blob/main/application/deployment.yaml
```

3. Display information about the Deployment:

```
kubectl describe deployment nginx-deployment

```
4. List the Pods created by the deployment:

```
kubectl get pods -l app=nginx
```
5. Display information about a Pod:

```
kubectl describe pod <pod-name>
```
where <pod-name> is the name of one of your Pods.


## Updating the deployment
1. Apply the new YAML file:

```
kubectl apply -f {DEPLOYMENT_UPDATE_FILE}
```
2. Watch the deployment create pods with new names and delete the old pods:

```
kubectl get pods -l app=nginx
```

## Scaling the application by increasing the replica count

1. Apply the new YAML file:

``` 
kubectl apply -f {DEPLOYMENT_SCALE_FILE}
```

2. Verify that the Deployment has four Pods:
```
kubectl get pods -l app=nginx
```

## Deleting a deployment

1. Delete the deployment by name:
```
kubectl delete deployment nginx-deployment
```