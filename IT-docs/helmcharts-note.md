Helm Charts Note
================



```
# infra-helm/index.yaml
helm repo add infra-helm https://artifactory.deepmap.ai/artifactory/infra-helm
```

helm repo list

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
```
