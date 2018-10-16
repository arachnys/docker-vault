# docker-vault

:whale: A custom, and up-to-date Vault Docker image for use with [vault-operator](https://github.com/helm/charts/tree/master/stable/vault-operator).

## Usage

```
apiVersion: "vault.security.coreos.com/v1alpha1"
kind: "VaultService"
metadata:
  name: "my-vault"
  namespace: "my-vault-namespace"
spec:
  nodes: 1
  # https://github.com/arachnys/docker-vault
  # https://hub.docker.com/r/arachnysdocker/vault/
  baseImage: "arachnysdocker/vault"
  version: "0.11.3"
```
