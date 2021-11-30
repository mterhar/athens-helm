# athens-server

Install Athens RTC server in Kubernetes

**Homepage:** <https://athensresearch.org>

## Source Code

* <https://github.com/athensresearch/athens>
* <https://github.com/fluree/ledger>

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` | Set affinity for the whole chart, includes Athens and Ledger |
| configEdn | string | `"{:password \"suchWow\"}"` | configEdn contains the configuration options in a lenghty string with escaped quotes. from https://github.com/athensresearch/athens/blob/main/src/clj/config.default.edn |
| fluree.image | object | `{"repository":"fluree/ledger","tag":"1.0"}` | Image used for fluree/ledger data storage |
| fluree.resources | object | `{}` | Set resources for the fluree/ledger statefulset pods |
| fluree.storageClassName | string | `""` |  |
| fluree.storageSize | string | `"10Gi"` | Set storage size for the ledger blockchain PVC |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"ghcr.io/athensresearch/athens"` | Image used for athens backend |
| image.tag | string | `"v2.0.0-beta.1"` |  |
| imagePullSecrets | list | `[]` | Set image pull secrets if needed |
| ingress.annotations | object | `{"nginx.ingress.kubernetes.io/proxy-connect-timeout":"7d","nginx.ingress.kubernetes.io/proxy-read-timeout":"7d","nginx.ingress.kubernetes.io/proxy-send-timeout":"7d"}` | Add ingress annotations. Default values fix a frequent timeout issue. |
| ingress.className | string | `""` | Set an ingress class name |
| ingress.enabled | bool | `false` | Create an ingress object to reference the ClusterIP Athens service |
| ingress.host | string | `""` | Set a host name that tells the ingress controller to route traffic to Athens Without the host value, ingress will try to route all traffic to Athens. |
| nodeSelector | object | `{}` | Set nodeSelector for the whole chart, includes Athens and Ledger |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` | Set podSecurityContext for athens pod. Fluree pod has fsGroup hard coded to work with the fluree/ledger user id: 1000 |
| resources | object | `{}` | Set Resource limits for Althens pod, Recommend 2048 mb of memory due to JVM configuration in https://github.com/athensresearch/athens/blob/main/script/docker-run-lan-party.sh#L3 |
| securityContext | object | `{}` |  |
| service.port | int | `3010` | Hard-coded in the athens image |
| service.type | string | `"ClusterIP"` | Sets the service type for Athens pod. Ledger pod is fixed as ClusterIP |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.create | bool | `true` | Specifies whether a service account should be created for Athens and Fluree/Ledger |
| serviceAccount.name | string | `""` | The name of the service account to use. If not set and create is true, a name is generated using the fullname template |
| tolerations | list | `[]` | Set tolerations for the whole chart, includes Athens and Ledger |
