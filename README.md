# WIP

```sh
# clone repo to docmost folder
git clone https://github.com/docmost/k8s docmost
```

## Install Traefik Ingress
```sh
# create traefik namespace
kubectl create namespace traefik

helm repo add traefik https://traefik.github.io/charts
helm repo update
helm install traefik traefik/traefik

kubectl apply -f traefik/access.yaml -n traefik
helm install -f values.yaml traefik traefik/traefik -n traefik
```

## Install cert manager for SSL (important cause distributed ssl not available in traefik community edition)
```
helm repo add jetstack https://charts.jetstack.io --force-update
helm install cert-manager jetstack/cert-manager --namespace cert-manager --create-namespace --version v1.18.0 --set crds.enabled=true
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.17.1/cert-manager.crds.yaml
kubectl apply -f issuer.yaml -n traefik
kubectl apply -f cert.yaml -n traefik
```

```sh
# clone repo to docmost folder
git clone https://github.com/docmost/k8s docmost

# create kubernetes namespace
kubectl create namespace docmost

# run the yaml file in the docmost directory
kubectl apply -f docmost -n docmost
```

Helpful commands:
```
# get pod details
kubectl describe pods -l app=docmost-app -n docmost

# view logs
kubectl logs deployment/docmost-app -n docmost
```


