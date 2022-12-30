## Create namespace CKAD

`kubectl create ns ckad`

```
namespace/ckad created
```

`kubectl config set-context --current --namespace=ckad`

## Create a pod in yaml format 

`kubectl run Pod1 --image nginx --port 80 --dry-run=client -o yaml > pod1.yaml`


`kubectl create -f pod1.yaml`

```
pod/pod1 created
```


`kubectl get pods -o wide -w`

```
NAME   READY   STATUS              RESTARTS   AGE   IP       NODE           NOMINATED NODE   READINESS GATES
pod1   0/1     ContainerCreating   0          43s   <none>   kind-worker2   <none>           <none>
pod1   1/1     Running             0          49s   10.244.2.2   kind-worker2   <none>           <none>

```
## Run a temporary pod using `busybox` shell into it and run a `wget`  against `pod1`


`kubectl run busybox --image busybox --rm -it -- bin/sh`


If you don't see a command prompt, try pressing enter.

/ # `wget 10.244.2.2`
```
Connecting to 10.244.2.2 (10.244.2.2:80)
saving to 'index.html'
index.html           100% |*********************************************************************************************************************************************************************************************************************|   615  0:00:00 ETA
'index.html' saved

```

## View the logs of pod1


`kubectl logs pod1`

```
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2022/12/29 11:46:15 [notice] 1#1: using the "epoll" event method
2022/12/29 11:46:15 [notice] 1#1: nginx/1.23.3
2022/12/29 11:46:15 [notice] 1#1: built by gcc 10.2.1 20210110 (Debian 10.2.1-6) 
2022/12/29 11:46:15 [notice] 1#1: OS: Linux 5.15.79.1-microsoft-standard-WSL2
2022/12/29 11:46:15 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2022/12/29 11:46:15 [notice] 1#1: start worker processes
2022/12/29 11:46:15 [notice] 1#1: start worker process 32
2022/12/29 11:46:15 [notice] 1#1: start worker process 33
2022/12/29 11:46:15 [notice] 1#1: start worker process 34
2022/12/29 11:46:15 [notice] 1#1: start worker process 35
10.244.1.3 - - [29/Dec/2022:12:37:21 +0000] "GET / HTTP/1.1" 200 615 "-" "Wget" "-"
```
