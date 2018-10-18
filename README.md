## What is this for?

This chart is meant to stub out `deployment`, `service` and `ingress` objects in a specific namespace. It will automatically create the `ingress` object with the needed annotations for use with the `alb-ingress` controller. Additionally, you need to set the `ingress.type` to either `internal` or `external` to decide if the ALB will be available only inside the Turner network or on the public internet.

## Usage

You _must_ define `namespace` and `ingress.type` at runtime, as there are no assigned defaults.

Example:
```
 ➜ helm install  . --set namespace=whiteboard-nonprod --set ingress.type=internal
```
This will create an internally available load balancer in the namespace `whiteboard-nonprod` with the host `whiteboard-nonprod-internal.cnnio.net`.

You can also override the default name generation with the additional flag `--set ingress.name=<your name here>`.
