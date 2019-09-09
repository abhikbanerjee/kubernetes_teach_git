# K8s Basic Logging

### Because we are using a shared environment, we need to create our resources in separate namespaces , with every command below please add the suffix "-n <yourname_bitbucket_ns>" for e.g (this assumes you have created your namespace already otherwise  run "create namespace <yourname_bitbucket_ns>"
```
# kubectl create -f rc.yaml -n abhik_bitbucket_ns
replicationcontroller "soaktestrc" created
```
## Logging Exercise

```
# This step has already been done
$ git clone https://github.com/shekhar2010us/kubernetes_teach_git.git
# go to k8s_logging
$ cd k8s_logging
```

### Run a pod and check logs
```
kubectl create -f basic-logging.yaml
```

### Check logs
```
kubectl logs pod/counter
```

### Destroy all resources
```
kubectl delete -f basic-logging.yaml
```

