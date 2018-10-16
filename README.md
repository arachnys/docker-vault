# docker-vault

[![](https://images.microbadger.com/badges/image/arachnysdocker/vault:0.11.3.svg)](https://microbadger.com/images/arachnysdocker/vault:0.11.3 "Get your own image badge on microbadger.com")

:whale: A custom, and up-to-date Vault Docker image for use with [Helm](https://helm.sh/) [vault-operator](https://github.com/helm/charts/tree/master/stable/vault-operator).

## Usage

**NOTE: `disable_mlock` must be set. See the `ConfigMap` below.**

```yml
---
kind: ConfigMap
apiVersion: v1
metadata:
  name: "my-vault-config"
  namespace: "my-vault-namespace"
  labels:
    app: vault
    vault_cluster: "my-vault"
data:
  # See https://hub.docker.com/_/vault/
  vault.hcl: |
    ui = true
    disable_mlock = true
---
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
  configMapName: "my-vault-config"
```
