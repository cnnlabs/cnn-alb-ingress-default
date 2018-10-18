## What is this for?

This chart is meant to stub out `deployment`, `service` and `ingress` objects in a specific namespace. It will automatically create the `ingress` object with the needed annotations for use with the `alb-ingress` controller. Additionally, you need to set the `ingress.type` to either `internal` or `external` to decide if the ALB will be available only inside the Turner network or on the public internet.

## Usage

You _must_ define `namespace` and `ingress.type` at runtime, as there are no assigned defaults.

Example:
```
 ➜ helm install  . --set namespace=whiteboard-nonprod --set ingress.type=internal
```
This will create an internally available load balancer in the namespace `whiteboard-nonprod` with the host `whiteboard-nonprod-internal.cnnio.net`.

## Initilizing an ALB for dedicated use

The syntax is exactly the same, but you'll need to add two additional flags: `--set app.name=<app name here> --namespace=<app name here>`.

Example:
```
 ➜ helm install . --set namespace=web-product-prod --set ingress.type=internal --set app.name=awesome-web-app --namespace=awesome-web-app
```

And yes, `--set namespace=foo` and `--namespace=bar` are both required. The first is the kubernetes namespace the resources will be created in, the other is the namespace helm/tiller are using to classify the resources we just created.
