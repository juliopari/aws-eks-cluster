# aws-eks

## 0. Realizar login con AWS CLI desde CMD
```
$ aws configure
AWS Access Key ID [****************CDFV]: <Se obtiene de security credentials>
AWS Secret Access Key [****************r+tf]: <Se obtiene de security credentials>
Default region name [us-east-1]: us-east-1 <Region del EKS creado>
Default output format [None]: <enter>
```

## 0. Descargar kubeconfig y ubicar en "C:\Users\USER\.kube" con nombre "config" sin extensión
```
C:\Users\USER\.kube\config
```

## 1. Listar namespace
```
kubectl get ns
```

## 2. Eliminar un namespace
```
kubectl delete ns <namespace>
```

## 3. Crear namespace node (ubicar en la carpeta /kubernetes/)
```
kubectl apply -f 00-namespace.yaml
```

## 4. Ejecutar deployment
```
kubectl -n nodejs-examples apply -f 01-nodejs-deployment-loadbalancer.yaml
```

## 4.1 Listar deployments
```
kubectl -n nodejs-examples get deployments
```

## 4.2 Listar services
```
kubectl -n nodejs-examples get services
```


## 5. Conocer la IP Pública: EXTERNAL-IP
```
kubectl -n nodejs-examples get services
```

```
NAME                   TYPE           CLUSTER-IP       EXTERNAL-IP                                                              PORT(S)        AGE
nodejs-invoke-reqres   LoadBalancer   10.100.188.142   aa12fa74c69fe4839bba58f7e0794a14-357419695.us-east-1.elb.amazonaws.com   80:31750/TCP   2m6s
```

## 7. Invocar a la API
```
POST
http://aa12fa74c69fe4839bba58f7e0794a14-357419695.us-east-1.elb.amazonaws.com/api/v1/single-user
{
    "id": 1
}
```

## 8. Invocar a la API
```
{
    "data": {
        "id": 1,
        "email": "george.bluth@reqres.in",
        "first_name": "George",
        "last_name": "Bluth",
        "avatar": "https://reqres.in/img/faces/1-image.jpg"
    },
    "support": {
        "url": "https://reqres.in/#support-heading",
        "text": "To keep ReqRes free, contributions towards server costs are appreciated!"
    }
}
```