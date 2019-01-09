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

# Dostanie się do poda

Wyświetlenie stdout i stderr z poda

`kubectl logs kuard`

Wyświetlenie stdout i stderr z poda i fallow
`kubectl logs -f  kuard`

Wejście do poda w trybie interaktywnym
`kubectl exec -it kuard sh`

Revers proxy do poda
`kubectl port-forward kuard 8080`

# DEMO 2 - zmienne zdefinowane w konfiguracji i referencje do obiektu

```
    env:
    - name: DEMO
      value: "Nasza wartosc"
```

```
  containers:
  - image: gcr.io/kuar-demo/kuard-amd64:1
    name: kuard
    ports:
    - containerPort: 8080
      name: http
      protocol: TCP
    env:
    - name: DEMO
      value: "Nasza wartosc"
```
## TO DO - dodac link do spec

```
    env:
    - name: DEMO
      value: "Nasza wartosc"
    - name: KUBE_POD_NAME
      valueFrom:
        fieldRef:
          fieldPath: metadata.name
    - name: KUBE_POD_IP
      valueFrom:
        fieldRef:
          fieldPath: status.podIP
    - name: KUBE_NODE_NAME
      valueFrom:
        fieldRef:
          fieldPath: spec.nodeName
```
