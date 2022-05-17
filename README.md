# grav-k8s
Kubernetes deployment of Grav CMS

# Deploy pod, pvc and service to Kubernetes
```
$ kubectl apply -f grav.yaml
```

# Install Grav on Persistent Volume (if you do not already have a Grav install) 
## Find version to install
https://github.com/getgrav/grav/tags
## Download, unzip and set persmission 
```
kubectl exec -it deployment/grav -- bash -c "curl -L  https://github.com/getgrav/grav/releases/download/1.7.33/grav-admin-v1.7.33.zip -o /tmp/grav.zip"
kubectl exec -it deployment/grav -- bash -c "unzip  /tmp/grav.zip -d /tmp"
kubectl exec -it deployment/grav -- bash -c "cp -rT /tmp/grav-admin /var/www/html/"
kubectl exec -it deployment/grav -- bash -c "rm -rf /tmp/grav.zip /tmp/grav-admin"
kubectl exec -it deployment/grav -- bash -c "chown -R www-data /var/www/html/"
```
