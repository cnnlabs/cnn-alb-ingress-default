## What is this for?

This chart is meant to stub out `deployment`, `service` and `ingress` objects in a specific namespace. It will automatically create the `ingress` object with the needed annotations for use with the `alb-ingress` controller. Additionally, if your `evironment` is `prod`, it will make the ALB available externally. Otherwise, it will only be available inside the Turner network.

## Usage

You _must_ define `project` and `environment` at runtime, as there are no assigned defaults.

Example:
```
 ➜ helm install  . --set project=whiteboard --set environment=stage
```
