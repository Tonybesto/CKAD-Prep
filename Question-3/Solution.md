kubectl create secret generic db-credentials --from-literal=db-password=speed
```
secret/db-credentials created
```

kubectl get secrets
```
NAME             TYPE     DATA   AGE
db-credentials   Opaque   1      7s
```

kubectl run sqlsvr --image nginx --dry-run=client -o yaml > q3.yaml

kubectl create -f q3.yaml

```
pod/sqlsvr created
```

kubectl exec -it sqlsvr -- bash


