# Tutorial: Jobs and CronJobs

### Because we are using a shared environment, we need to create our resources in separate namespaces , with every command below please add the suffix "-n <yourname-bitbucket-ns>" for e.g (this assumes you have created your namespace already otherwise  run "create namespace <yourname-bitbucket-ns>"
```
# kubectl create -f rc.yaml -n abhik-bitbucket-ns
replicationcontroller "soaktestrc" created
```

In this tutorial we will learn how to create Jobs, CronJobs and inspect the containers and logs.

### Create a simple job 

```
# cd to ex9
kubectl create -f simplejob.yaml
```

Check for jobs, pods running

```
$ kubectl get jobs,po,svc
```

Check logs and describe the pods

```
$ kubectl describe job countdown

$ kubectl describe pod <countdown-pod_name>

$ kubectl logs pod <countdown-pod_name>
```

### Create a Cron Job

```
$ kubectl create -f cronjob.yaml 
```
Check for the running cronjob,pods,svc

```
$ kubectl get po,cronjob
```
Check if the pods are running and the age of the cronjob periodically (the LAST SCHEDULE should get reset every minute)
To get all pods that may have been completed use this 
```
$ kubectl get po,cronjob --show-all
```
Do a describe on the pods and check the logs

```
$ kubectl describe cronjob periodiccron

$ kubectl logs pod <pod_name> 

```
Edit the cronjob - Disable it

```
$ kubectl edit cronjob periodiccron

change the flag to suspend to true, save and exit

$ kubectl get cronjobs -o wide
```
The suspended column should show as true, and the cron job should stop executing and stop creating new pods

