# Lab 6 - Kubernetes

## Commends used:

1. Start Minikube
```
minikube start --driver=docker
```
2. Install NFS Server Provisioner via Helm
```
helm repo add stable https://charts.helm.sh/stable
helm repo update

helm install nfs-server stable/nfs-server-provisioner --set storageClass.name=nfs --set persistence.enabled=true --set persistence.size=1Gi
```
3. Deploy the App
```
kubectl apply -f pvc.yaml
kubectl apply -f nginx-deployment.yaml
kubectl apply -f nginx-service.yaml
kubectl apply -f copy-job.yaml
```
4. Access the App
```
minikube ip
```

For some reason, I couldn't connect to the service directly, so I had to set up port forwarding to access it.
```
minikube service nginx-service
```
5. Testing the App
```
kubectl get pods
kubectl get storageclass
kubectl get svc
kubectl get jobs
```
