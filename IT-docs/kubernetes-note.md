Kubernetes(K8s) Note
====================

kubectl get ns
cat ~/.kube/config
kubectl --context <k8s-context> get [namespace|ns]
kubectl --context <k8s-context> -n <namespace> get [service|svc]
kubectl --context <k8s-context> -n <namespace> get [ingress|ing]
kubectl --context <k8s-context> -n <namespace> get pods
kubectl --context <k8s-context> -n <namespace> get deploy <service> -o yaml
kubectl --context <k8s-context> -n <namespace> get service <service>
kubectl --context <k8s-context> -n <namespace> port-forward svc/<service> 8080:8080
kubectl --context <k8s-context> -n <namespace> exec -it <pod> /bin/sh
