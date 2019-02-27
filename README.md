## What is this for?

This chart is meant to stub out `deployment`, `service` and `ingress` objects in a specific
namespace. It will automatically create the `ingress` object with the needed annotations for use
with the `alb-ingress` controller. Additionally, you need to set the `ingress.type` to either
`internal` or `external` to decide if the ALB will be available only inside the Turner network or
on the public internet.

## Usage

Example:
```
 ➜ helm install . \
    --name=web-product-prod-private-shared-eks-prime \
    --namespace=web-product-prod \
    --set ingress.cluser=eks-prime \
    --set ingress.domain=cnnio.net \
    --set ingress.securityGroup=cnn-eks-prime-private \
    --set ingress.bucketName=alb-logs-cnn-eks-prime \
    --set ingress.type=private
```
This will create an internally available load balancer in the namespace `web-product-prod` with
the host `web-product-prod-private-shared-eks-prime.cnnio.net`.

## Initilizing an ALB with a different name

The syntax is exactly the same, but you'll need to add one additional flag:
`--set overrideName=<app name here>`. 

Example:
```
 ➜ helm install . \
    --name=web-product-prod-private-shared-eks-prime \
    --namespace=web-product-prod \
    --set ingress.cluser=eks-prime \
    --set ingress.domain=cnnio.net \
    --set ingress.securityGroup=cnn-eks-prime-private \
    --set ingress.bucketName=alb-logs-cnn-eks-prime \
    --set ingress.type=private \
    --set overrideName=awesome-web-app
```
