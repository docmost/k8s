```sh
# clone repo to docmost folder
git clone https://github.com/docmost/k8s docmost

# create kubernetes namespace
kubectl create namespace docmost

# run the yaml file in the docmost directory
kubectl apply -f docmost -n docmost
```

Other helpful commands:
```
# get pod details
kubectl describe pods -l app=docmost-app -n docmost

# view logs
kubectl logs deployment/docmost-app -n docmost
```
