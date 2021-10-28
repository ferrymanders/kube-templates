# kube-templates

## nginx
```
namespace=nginx-php-test
location=https://raw.githubusercontent.com/ferrymanders/kube-templates/main/nginx-php

kubectl create -n $namespace -f ${location}/01-cm-nginx-config.yaml
kubectl create -n $namespace -f ${location}/01-cm-php-fpm-config.yaml
kubectl create -n $namespace -f ${location}/05-deployment.yaml
kubectl create -n $namespace -f ${location}/06-service.yaml

# Add ingressroute if needed
name="route-name"
hostname="sub.example.tld"
servicename="service-name"
namespace="app-namespace"
port="8080"
tlssecret="tls-sub-domain-tld"

curl -s ${location}/09-ingressroute.yaml \
  | sed -e "s/__NAME__/$name/" \
        -e "s/__HOSTNAME__/$hostname/" \
        -e "s/__SERVICENAME__/$servicename/" \
        -e "s/__NAMESPACE__/$namespace/" \
        -e "s/__PORT__/$port/" \
        -e "s/__TLSSECRET__/$tlssecret/" \
  | kubectl create -f -
```
