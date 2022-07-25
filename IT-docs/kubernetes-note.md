Kubernetes(K8s) Note
====================

```bash
kubectl get ns
cat ~/.kube/config

NAMESPACE=--context <k8s-context> -n <namespace>
kubectl $NAMESPACE get [namespace|ns]
kubectl $NAMESPACE get [service|svc]
kubectl $NAMESPACE get [ingress|ing]
kubectl $NAMESPACE get [deployments|deploy]
kubectl $NAMESPACE get pods
kubectl $NAMESPACE get configmaps
kubectl $NAMESPACE get deploy <service> -o yaml
kubectl $NAMESPACE get service <service>
kubectl $NAMESPACE describe pods/<pod>
kubectl $NAMESPACE edit configmaps/<config>
kubectl $NAMESPACE port-forward svc/<service> 8080:8080
kubectl $NAMESPACE exec -it <pod> /bin/sh
kubectl $NAMESPACE get replicaset
kubectl $NAMESPACE describe replicaset <relicaset_name>

kubectl --context dev.deepmap.ai -n project-mapshop delete deploy mapshop

kubectl cp <pod>:/path /local/path/

kubectl get deploy | grep <dep>
kubectl scale --replicas=1 deploy <dep>
kubectl rollout restart deployment <dep>
kubectl rollout history deploy go-anga
kubectl rollout undo deploy go-anga --to-revision=1

kubectl annotate pods <pod> app-version="2" --overwrite
kubectl delete pods --field-selector=status.phase=Failed
kubectl set env deployment <dep> APP_VERSION="2"
kubectl logs <pod> --all-containers

kubectl get configmaps/map-factory-job-config
kubectl edit configmaps/map-factory-job-config



kubectl get pods -o jsonpath='{range .items[*]}{@.metadata.name}{" "}{@.spec.containers[*].image}{"\n"}{end}'| column -t
```
