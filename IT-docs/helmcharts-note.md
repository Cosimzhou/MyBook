Helm Charts Note
================



```
# URL 下是需要一个 index.yaml 文件
helm repo add infra-helm https://artifactory.deepmap.ai/artifactory/infra-helm

helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo add jenkins https://charts.jenkins.io
helm repo update
```

helm install [RELASE_NAME] jenkins/jenkins [flags]
   or: helm uninstall [RELASE_NAME]
helm upgrade [RELEASE_NAME] jenkins/jenkins [flags]
helm show values jenkins/jenkins

helm pull <repo>/<chart> --version <version>
helm pull bitnami/keycloak --version 7.0.1

helm repo list

helm repo update

helm search repo infra-helm --devel


helm-secrets dec /path/to/secrets.yaml

sops /path/to/secrets.yaml

gpg --import pgp_public_key.txt
gpg --import pgp_private_key.txt

gpg --key-gen
gpg --fingerprint



```
export MAPSHOP_CHART_VERSION=1.1.1180-g5602ad2529
export MAPSHOP_VERSION=v1.1-1178-gdee56c8bf1
helmfile --namespace anga \
         --kube-context staging.deepmap.ai \
         --environment staging \
         -f helmfile_cradle/mapshop/helmfile.yaml \
         --output-dir testoutput \
         template
helmfile --namespace anga \
         --kube-context staging.deepmap.ai \
         --environment staging \
         -f helmfile_cradle/mapshop/helmfile.yaml \
         sync




MAPSHOP_VERSION=v1.1-1386-g5d88cb5ab4 NAMESPACE=project-mapshop DATA_NAMESPACE=project_mapshop MAPSHOP_CHART_CHART_VERSION=1.1.1398-g442f33f464 MAPSHOP_CHART_VERSION=1.1.1398-g442f33f464 helmfile --namespace project-mapshop --kube-context default-context --environment individual-dev -f deepmap-deploy/helmfile_cradle/mapshop/helmfile.yaml template
```
