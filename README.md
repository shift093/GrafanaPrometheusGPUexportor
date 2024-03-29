# GrafanaPrometheusGPUexportor

![Alt text](/img/dashboard.jpg "Gpu monitoring dashboard")

![Alt text](/img/S__31883305.jpg)

## Prerequested
 ### STEP0.clone下載
 ```
 cd ~/Downloads
 git clone https://github.com/shift093/GrafanaPrometheusGPUexportor.git
 cd ~/Downloads/GrafanaPrometheusGPUexportor/1.18.4
 ```
 ### STEP1.安裝microk8s
 ```
 sudo snap install microk8s --classic --channel=1.19/stable
 sudo apt-get install iptables-persistent -y
 sudo iptables -P FORWARD ACCEPT
 sudo ufw allow in on cbr0 && sudo ufw allow out on cbr0
 sudo microk8s.status
 sudo microk8s.enable istio gpu ingress dns
 (optional)sudo snap alias microk8s.kubectl kubectl
 (optional)sudo reboot now
 ```
 ### STEP2.k8s腳本
 ```shell
 sudo microk8s.kubectl label nodes gpu hardware-type=NVIDIAGPU
 sudo microk8s.kubectl get nodes --show-labels
 sudo microk8s.kubectl create namespace monitoring
 sudo microk8s.kubectl apply -f prometheus-configmap.yaml
 sudo microk8s.kubectl apply -f prometheus-deployment.yaml
 sudo microk8s.kubectl apply -f gpu-node-exporter-daemonset.yaml
 watch sudo microk8s.kubectl get pod --all-namespaces
 ```
 ### STEP3.進入Grafana
 ```
 cd GrafanaPrometheusGPUexportor
 wget https://s3-us-west-2.amazonaws.com/grafana-releases/release/grafana-5.3.2.linux-amd64.tar.gz
 tar -zxvf grafana-5.3.2.linux-amd64.tar.gz
 ~/Downloads/grafana/grafana-5.4.3/bin/grafana-server
 
 curl localhost:3000
 curl localhost:9100
 curl localhost:9090
 
 or
 
 
 sudo lsof -i -P -n | grep :9090
 sudo lsof -i -P -n | grep :3000
 sudo lsof -i -P -n | grep :9100
 
 #dashboard id:9957
 #Finished!
 ```
 
### Delete all service&pod
```
cd GrafanaPrometheusGPUexportor
sudo microk8s.kubectl delete -f .
sudo microk8s.kubectl delete namespace monitoring
```

### Rebuild monitoring system
```
```

### Disable microk8s
```
sudo snap disable microk8s
```
 
### Remove microk8s
```
sudo snap remove microk8s --purge
```

### Refresh
```
sudo snap refresh microk8s  --channel=1.18/stable
sudo snap refresh microk8s  --channel=1.15/stable
```

### Refernece

https://www.lagou.com/lgeduarticle/111606.html
