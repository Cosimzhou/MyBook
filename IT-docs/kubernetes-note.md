Kubernetes(K8s) Note
====================

```bash
kubectl get ns
cat ~/.kube/config

POD_NAMESPACE := -n <namespace>

NAMESPACE=--context <k8s-context> -n <namespace>
kubectl $NAMESPACE get [namespace|ns]
kubectl $NAMESPACE get [service|svc]
kubectl $NAMESPACE get [ingress|ing]
kubectl $NAMESPACE get [deployments|deploy]
kubectl $NAMESPACE get pods
kubectl $NAMESPACE get configmaps
kubectl $NAMESPACE get deploy <service> -o yaml
kubectl $NAMESPACE get service <service>
kubectl $NAMESPACE get secret <secret>
kubectl $NAMESPACE describe pods/<pod>
kubectl $NAMESPACE edit configmaps/<config>
kubectl $NAMESPACE port-forward svc/<service> 8080:8080
kubectl $NAMESPACE exec -it <pod> /bin/sh
kubectl $NAMESPACE get replicaset
kubectl $NAMESPACE describe replicaset <relicaset_name>

kubectl --context dev.deepmap.ai -n project-mapshop delete deploy mapshop
kubectl delete cronjob mapshop-job

kubectl cp <pod>:root/path/file /local/path/file

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


kubectl attach mypod         # Get output from running pod mypod;
                             # use the 'kubectl.kubernetes.io/default-container' annotation
                             # for selecting the container to be attached or the first
                             # container in the pod will be chosen
kubectl attach rs/nginx      # Get output from the first pod of a replica set named nginx

kubectl attach mypod -c ruby-container       # Get output from ruby-container from pod mypod
kubectl attach mypod -c ruby-container -i -t # Switch to raw terminal mode; sends stdin to 'bash'
                                             # in ruby-container from pod mypod # and sends
                                             # stdout/stderr from 'bash' back to the client

kubectl top node             # Show metrics for all nodes
kubectl top node <NODE_NAME> # Show metrics for a given node


kubectl get pods -o jsonpath='{range .items[*]}{@.metadata.name}{" "}{@.spec.containers[*].image}{"\n"}{end}'| column -t

kubectl get <pod_name> -o yaml

kubectl getsecret <secret-name> -o jsonpath='{.data}'


kubectl get deployments,statefulsets,daemonsets,cronjobs,jobs,pods -n namespace-name -o yaml
```



## get

```
kubectl get pods   # List all pods in ps output format
kubectl get pods -o wide  # List all pods in ps output format with more information (such as node name)
kubectl get pod test-pod -o custom-columns=CONTAINER:.spec.containers[0].name,IMAGE:.spec.containers[0].image # List resource information in custom columns
kubectl get pod web-pod-13je7 --subresource status # List status subresource for a single pod.

kubectl get replicationcontroller web # List a single replication controller with specified NAME in ps output format

kubectl get deployments.v1.apps -o json # List deployments in JSON output format, in the "v1" version of the "apps" API group

kubectl get -o json pod web-pod-13je7 # List a single pod in JSON output format

kubectl get -f pod.yaml -o json # List a pod identified by type and name specified in "pod.yaml" in JSON output format

kubectl get -k dir/ # List resources from a directory with kustomization.yaml - e.g. dir/kustomization.yaml

kubectl get -o template pod/web-pod-13je7 --template={{.status.phase}} # Return only the phase value of the specified pod

kubectl get rc,services # List all replication controllers and services together in ps output format

kubectl get rc/web service/frontend pods/web-pod-13je7 # List one or more resources by their type and names

```
