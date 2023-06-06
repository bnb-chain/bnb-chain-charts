# greenfield-validator-charts
Helm chart repository for the greenfield-validator

## To deploy:
1. `helm repo add bnb-chain https://chart.bnbchain.world/`
2. `helm repo update`
3. `helm install greenfield-validator bnb-chain/gnfd-validator`

## To note:

Please refer to the `values.yaml` description section in case of any error faced in step 3 above.

Please install this Helm Chart in the directory containing the `a-config-config/` directory. This allows the `ConfigMap` to grab all files and transfer to the right folder in the pod.

Please also ensure you have VMServiceScrape CRD installed in your cluster, else, the helm chart cannot install and deploy the resources below into your cluster.

## `values.yaml` Description

Our image is pulled from `ghcr.io/bnb-chain/greenfield`. Using other images could lead to an error.

Our `storageClassName` is `ebs-sc`, with a `volumeSize` of `500Gi`.

If you are downloading a genesis file for greenfield, put that link in the `url` stated under `genesisInit`. Otherwise, defaults to copying the genesis.json from the `a-config/config` directory.

The `podSecurityContext` and the `securityContext` used help to prevent any internal file system modifications as it prevent root user permissions.

At the very end, there is an option to `enableConfigMapInit`, this config refers to the `configPath` in the [repo where the genesis document is provided](https://github.com/bnb-chain/bnbchain-gitops/tree/main/apps/gnfd-validator-qa). Change the `configPath` if necessary.

## Common Operations

### Check Pod Status

```
$ kubectl get pod
```

You should see a `2/2` pod running for the validator. This means there are 2 containers running for the validator.

To see more details about a pod, you can describe it:

```
$ kubectl describe pod <POD_NAME> 
```

### Check the Pod Logs 

```
$ kubectl logs <POD_NAME> -c <CONTAINER_NAME>
```

