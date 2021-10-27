# kube-templates

## nginx
```
namespace=nginx-php-test
location=https://raw.githubusercontent.com/ferrymanders/kube-templates/main/nginx-php

kubectl create -n $namespace -f ${location}/01-cm-nginx-config.yaml
kubectl create -n $namespace -f ${location}/01-cm-php-fpm-config.yaml
kubectl create -n $namespace -f ${location}/05-deployment.yaml
kubectl create -n $namespace -f ${location}/06-service.yaml
```