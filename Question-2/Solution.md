# Create a new config map named db-config from an env file

`kubectl create configmap db-config --from-env-file=config.txt`

# Check to see the created configmap

`kubectl get configmap db-config`

```
NAME               DATA   AGE
db-config          2      9s
```

# Create a Pod named `sqlsvr` that uses the environment variables from the configmap and runs a container using image of  `nginx`

`kubectl run sqlsvr --image nginx --dry-run=client -o yaml > q2.yaml`

# Check the  q2.yaml file to locate the configmap 

# Exec into the pod and display the create environment variables.

`kubectl exec -it sqlsvr sh`
```
kubectl exec [POD] [COMMAND] is DEPRECATED and will be removed in a future version. Use kubectl exec [POD] -- [COMMAND] instead.
# ls

bin  boot  dev  docker-entrypoint.d  docker-entrypoint.sh  etc home  lib  lib64  media  mnt  opt  proc  product_uuid  root  run  sbin   srv  sys  tmp  usr  var
# cd bin

# ls 
bash   chmod  dash  df     dnsdomainname  egrep  findmnt  gzexe     ln     lsblk  mktemp  mountpoint     pidof  readlink  run-parts  sleep  sync      touch   uname       wdctl         zcmp    zfgrep  zless
cat    chown  date  dir    domainname     false  grep     gzip     login  mkdir  more     mv             pwd rm   sed        stty   tar       true    uncompress  ypdomainname  zdiff   zforce  zmore
chgrp  cp     dd    dmesg  echo        fgrep  gunzip   hostname  ls        mknod  mount   nisdomainname  rbash  rmdir     sh         su     tempfile  umount  vdir        zcat          zegrep  zgrep   znew
```