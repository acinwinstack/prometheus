# prometheus on kubernetes
   
   
   
### 創建nfs空間
```
mkdir -p /nfs/prometheus
echo "/nfs/prometheus *(rw,no_subtree_check,sync,all_squash,anonuid=0,anongid=0)" >> /nfs/exports
```

### 下載
```
git clone https://github.com/acinwinstack/prometheus.git
cd prometheus
```

### 修改prometheus-deploy.yaml
```
          nfs:
            server: <NFS_IP>
            path: "/nfs/prometheus"
```

### 佈署prometheus
```
kubectl create -f node-exporter.yaml
kubectl create -f rbac-setup.yaml.yaml
kubectl create -f prometheus-config-map.yaml
kubectl create -f prometheus-deploy.yaml
```




