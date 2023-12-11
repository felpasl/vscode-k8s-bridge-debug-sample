# Debug bridge to kubernetes

Using https://learn.microsoft.com/en-us/visualstudio/bridge/bridge-to-kubernetes-vs-code bridge-to-kubernetes

We are able to run a local debug environment but proxying all inputs/outputs from a kubernetes pod
acessing in debuging instance a real environment,

> "Bridge to Kubernetes allows you to run and debug code on your development computer. That computer is still connected to your Kubernetes cluster with the rest of your application or services. If you have a large microservices architecture with many interdependent services and databases, replicating those dependencies on your development computer can be difficult. Building and deploying code to your Kubernetes cluster for each code change can be slow, time-consuming, and difficult."

## Run

Apply on your kubernetes the `DebugKube-Sample.yaml` file with service and deployment

the service will be related to vscode task: `bridge-to-kubernetes.service` 

```json
{
    "label": "bridge-to-kubernetes.service",
    "type": "bridge-to-kubernetes.service",
    "dependsOn": [
        "build",
    ],
    "service": "debug-kube-sample",
    "targetNamespace": "default",
    "ports": [
        5255
    ],
    "useKubernetesServiceEnvironmentVariables": true
}
```
the Launch action `.NET Core Launch (bridge)` trigger the task starting a new Pod to proxy requests inside the current kubernetes context.
