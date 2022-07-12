### 安装 K3S

`curl -sfL https://get.k3s.io | sh -`{{execute T1}}

```shell
mkdir $HOME/.kube
sudo cp /etc/rancher/k3s/k3s.yaml $HOME/.kube/config
sudo chmod 644 $HOME/.kube/config
```{{execute T1}}

### 获取节点状态

`kubectl get nodes`{{execute T1}}

输出如下信息

```
NAME     STATUS   ROLES                  AGE     VERSION
ubuntu   Ready    control-plane,master   5m27s   v1.23.8+k3s1
```

### 安装 Helm

下载 helm 并且安装到 `/usr/local/bin/`

```shell

wget https://get.helm.sh/helm-v3.8.1-linux-amd64.tar.gz

tar -zxvf helm-v3.8.1-linux-amd64.tar.gz && mv linux-amd64/helm /usr/local/bin/helm

kubectl -n kube-system create serviceaccount tiller
 
kubectl create clusterrolebinding tiller --clusterrole cluster-admin --serviceaccount=kube-system:tiller 
```{{execute T1}}

`helm --help`{{execute T1}}


