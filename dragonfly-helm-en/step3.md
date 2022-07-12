
Pull demo images and wait it done

`time k3s crictl pull registry.cn-hangzhou.aliyuncs.com/alidragonfly/supernode:0.2.0`{{execute T1}}

Watching dfdaemon log

`kubectl -n dragonfly-system exec -it $(kubectl -n dragonfly-system get pods --no-headers -o custom-columns=":metadata.name" -l component=dfdaemon | head -n1 ) -- cat /var/log/dragonfly/daemon/core.log`{{execute T2}}

Remove demo image

`k3s crictl rmi registry.cn-hangzhou.aliyuncs.com/alidragonfly/supernode:0.2.0`{{execute T1}}

Rerun the pull command line

`time k3s crictl pull registry.cn-hangzhou.aliyuncs.com/alidragonfly/supernode:0.2.0`{{execute T1}}

Pickup `peer task done` log from `/var/log/dragonfly/daemon/core.log`

`kubectl -n dragonfly-system exec -it $(kubectl -n dragonfly-system get pods --no-headers -o custom-columns=":metadata.name" -l component=dfdaemon | head -n1 ) -- grep "peer task done" /var/log/dragonfly/daemon/core.log`{{execute T2}}
