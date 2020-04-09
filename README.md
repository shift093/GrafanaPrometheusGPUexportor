# GrafanaPrometheusGPUexportor

![Alt text](/img/dashboard.jpg "Gpu monitoring dashboard")

## Prerequested
 ### STEP0.clone下載
 ```
 git clone https://github.com/shift093/GrafanaPrometheusGPUexportor.git
 ```
 ### STEP1.安裝microk8s
 ```
 sudo snap install microk8s --classic
 sudo  microk8s.status
 sudo microk8s.enable istio gpu 
 ```
 ### STEP2.k8s腳本
 ```shell
 sudo microk8s.kubectl label nodes $hostname hardware-type=NVIDIAGPU
 sudo microk8s.kubectl get nodes --show-labels
 sudo microk8s.kubectl create namespace monitoring
 sudo microk8s.kubectl apply -f .
 sudo microk8s.kubectl get pod
 ```
 ### STEP3.進入Grafana
 ```
 curl localhost:3000#admin/admin
 #dashboard id:9957
 #Finished!
 ```
