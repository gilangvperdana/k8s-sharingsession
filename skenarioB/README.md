# Note

## Deplyoment
- Create Deployment, Service, Configmap & Ingress with PV

## Deployment2
- Create Deployment, Service, Configmap & Ingress with PV

## Deployment3
- Create HPA for Deployment2

## AutoScaling
```
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
kubectl patch deployment metrics-server -n kube-system --type 'json' -p '[{"op": "add", "path": "/spec/template/spec/containers/0/args/-", "value": "--kubelet-insecure-tls"}]'
kubectl run -i --tty load-generator --rm --image=busybox --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://172.20.50.16; done"
```