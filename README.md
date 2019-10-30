# GrafanaPrometheusGPUexportor

## Prerequested

 1.安裝microk8s
 
```shell
kubectl label nodes gpu hardware-type=NVIDIAGPU
kubectl get nodes --show-labels
kubectl create namespace monitoring
kubectl apply -f ./*.yaml

```
