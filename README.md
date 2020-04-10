# GrafanaPrometheusGPUexportor

![Alt text](/img/dashboard.jpg "Gpu monitoring dashboard")

![Alt text](/img/S__31883305.jpg)

## Prerequested
 ### STEP0.clone下載
 ```
 git clone https://github.com/shift093/GrafanaPrometheusGPUexportor.git
 cd GrafanaPrometheusGPUexportor
 ```
 ### STEP1.安裝microk8s
 ```
 sudo snap install microk8s --classic --channel=1.18/stable
 or 
 sudo snap install microk8s --classic --channel=1.17.2/stable

 sudo apt-get install iptables-persistent
 sudo iptables -P FORWARD ACCEPT
 sudo ufw allow in on cbr0 && sudo ufw allow out on cbr0
 sudo microk8s.status
 sudo microk8s.enable istio gpu ingress dns
 (optional)sudo snap alias microk8s.kubectl kubectl
 (optional)sudo reboot now
 ```
 ### STEP2.k8s腳本
 ```shell
 sudo microk8s.kubectl label nodes $hostname hardware-type=NVIDIAGPU
 sudo microk8s.kubectl get nodes --show-labels
 sudo microk8s.kubectl create namespace monitoring
 sudo microk8s.kubectl apply -f .
 watch sudo microk8s.kubectl get pod
 ```
 ### STEP3.進入Grafana
 ```
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
sudo microk8s.kubectl delete namespace monitorin
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
