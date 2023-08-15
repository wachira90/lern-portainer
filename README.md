# Portainer CE Kubernetes

https://portainer.github.io/k8s/

## install command

```
helm repo add portainer https://portainer.github.io/k8s/
helm repo update
```

## NodePort
helm upgrade --install --create-namespace -n portainer portainer portainer/portainer --set tls.force=true


## ingress

```
helm upgrade --install --create-namespace -n portainer portainer portainer/portainer \
    --set service.type=ClusterIP \
    --set tls.force=true \
    --set ingress.enabled=true \
    --set ingress.ingressClassName=<ingressClassName (eg: nginx)> \
    --set ingress.annotations."nginx\.ingress\.kubernetes\.io/backend-protocol"=HTTPS \
    --set ingress.hosts[0].host=<fqdn (eg: portainer.example.io)> \
    --set ingress.hosts[0].paths[0].path="/"
```

## LoadBalance


Using the following command, Portainer will be available at an assigned Load Balancer IP on port 9443 for HTTPS:

```
helm upgrade --install --create-namespace -n portainer portainer portainer/portainer \
    --set service.type=LoadBalancer \
    --set tls.force=true
```


https://docs.portainer.io/start/install-ce/server/kubernetes/baremetal



