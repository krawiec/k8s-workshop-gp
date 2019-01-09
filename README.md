# k8s-workshop-gp

# Logowanie do azure

```
az login
az account list -o table
az account set -s id subskrypcji
az account show
```

# Pobieranie konfigu do k8s

```
az aks get-credentials --resource-group aks-labki --name aks-labki
```

# demo1

Wrzucenie konfiguracji na klaster

`kubectl apply -f demo1.yaml`

Listowanie podów

`kubectl get pods`

Listowanie podów z ip i nodem

`kubectl get pods -o wide`
