# kube

kubernetes test project.

## use command

### kubernetes dashboard

```shell
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0/aio/deploy/recommended.yaml
kubectl proxy
kubectl apply -f deployments/credentials/service-account.yaml
kubectl -n kube-system get secret
kubectl -n kube-system describe secret admin-user-token-xxxxx
```

### deploy and delete

```shell
# get resources
kubectl get nodes
kubectl get namespace

# pod
kubectl apply -f deployments/pod/sample.yaml
kubectl exec -it sample-pod sh
kubectl delete pod sample-pod
kubectl delete -f deployments/pod/sample.yaml

# deployment
kubectl apply -f deployments/deployment/sample.yaml
kubectl rollout history deployment
kubectl rollout undo deployment
kubectl delete -f deployments/deployment/sample.yaml
```

## note

* Minimum resource in kubernetes is `pod`.
* A `pod` can contain multiple containers.
* A container in one `pod` cannot be traversed by multiple `nodes`.
* Each `pod` will be assigned a unique virtual IP address.
* You can use localhost for access between containers in a `pod`.
* To increase the availability of a `pod`, you can use a `replica set`.
* The `replica set` allows you to duplicate and manage your pods.
* In actual operation, it is recommended to use the higher-level concept of `deployment` instead of `replica sets`.
* In kubernetes, `deployment` are performed as one unit.
* If a problem is found after deployment, rollback can be done with `kubectl rollout undo deployment`.
*