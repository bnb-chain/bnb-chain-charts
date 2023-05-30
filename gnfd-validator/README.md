# geenfield-validator-charts
Helm chart repository for the greenfield-validator

## To note:
Please ensure you have VMServiceScrape CRD installed in your cluster, else, the helm chart cannot install and deploy the resources below into your cluster.

## Resource Descriptions

Below is a list of the Kubernetes resources created by this helm chart.

The resources created by this helm chart will be prefixed with the helm release name. Below, they are denoted by the `<RELEASE_NAME>` prefix.

StatefulSet:
* `<RELEASE_NAME>-validator` - The validator StatefulSet

Services:
* `<RELEASE_NAME>-validator` - The validator Service

ConfigMaps:
* `<RELEASE_NAME>-nodekey` - The validator nodekey
* `<RELEASE_NAME>-config` - The validator configuration

Secrets:
* `<RELEASE_NAME>-private-key` - The validator private-key, it is an ExternalSecret

Ingress:
* `<RELEASE_NAME>-ingress` - The validator ingress, which controls network access to the validator pods

ServiceMonitor:
* `<RELEASE_NAME>-validator` - The validator ServiceMonitor

PodDisruptionBudget:
* `<RELEASE_NAME>-validator` - The PodDisruptionBudget for validator

## Common Operations

### Check Pod Status

```
$ kubectl get pod
```

You should see at least `1/1` pod running for the validator. If there are any restarts, you should see it in this view.

To see more details about a singular pod, you can describe it:

```
$ kubectl describe pod <POD_NAME>
```

### Check the Pod Logs

```
$ kubectl logs <POD_NAME>
```

### Check all services

```
$ kubectl get services
```
