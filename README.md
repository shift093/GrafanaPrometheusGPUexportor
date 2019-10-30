# GrafanaPrometheusGPUexportor

## Prerequested
 STEP0.
 ```
 git clone https://github.com/shift093/GrafanaPrometheusGPUexportor.git
 ```
 STEP1.安裝microk8s
 sudo snap install microk8s --classic
 
 STEP2.
```shell
kubectl label nodes gpu hardware-type=NVIDIAGPU
kubectl get nodes --show-labels
kubectl create namespace monitoring
kubectl apply -f ./*.yaml

```
