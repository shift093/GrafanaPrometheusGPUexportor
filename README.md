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
 ```
 ### STEP2.k8s腳本
 ```shell
 kubectl label nodes gpu hardware-type=NVIDIAGPU
 kubectl get nodes --show-labels
 kubectl create namespace monitoring
 kubectl apply -f ./*.yaml
 ```
 ### STEP3.進入Grafana
 curl localhost:3000
 dashboard id:9957
 Finished!
