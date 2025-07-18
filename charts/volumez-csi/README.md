# volumez-csi

![Version: 1.33.0-rc.1](https://img.shields.io/badge/Version-1.33.0--rc.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.16.0](https://img.shields.io/badge/AppVersion-1.16.0-informational?style=flat-square)

A Helm chart for Volumez-CSI Driver

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| envId | string | `""` |  |
| vlzAuthToken | string | `""` | CSI Driver Token (Refresh Token) |
| verboseLevel | int | `0` |  |
| vlzCsiDriver.repository | string | `"public.ecr.aws/u0q8u2v6/volumez-csi"` |  |
| vlzCsiDriver.tag | string | `"v1.18.0-rc.1"` |  |
| vlzCsiDriver.fsGroupPolicy | string | `"File"` |  |
| vlzSnapshotRollbackController.repository | string | `"public.ecr.aws/u0q8u2v6/vlz-snapshotrollback-controller"` |  |
| vlzSnapshotRollbackController.tag | string | `"v1.3.0"` |  |
| vlzEndpoint.apiUrl | string | `"api.volumez.com"` | {custom-id}.execute-api.{region}.amazonaws.com |
| vlzEndpoint.basePath | string | `""` | Example: "dev" |
| multiInstanceMode | bool | `false` | Allows multiple deployments of the CSI driver on the same cluster |
| vlzConnector.repoUrl | string | `"https://signup.volumez.com/connector/"` |  |
| vlzConnector.forceInstall | bool | `false` |  |
| vlzConnector.domain | string | `"connector.volumez.com"` |  |
| sidecars.attacher.tag | string | `"v4.7.0"` |  |
| sidecars.attacher.workers | int | `10` |  |
| sidecars.registrar.tag | string | `"v2.12.0"` |  |
| sidecars.provisioner.tag | string | `"v5.1.0"` |  |
| sidecars.snapshotter.tag | string | `"v8.2.0"` |  |
| sidecars.snapshotController.tag | string | `"v8.2.0"` |  |
| sidecars.resizer.tag | string | `"v1.9.0"` |  |
| controller | object | `{"nodeSelector":null,"tolerations":null}` | Allows to install the controller and sidecars on a specific node or node group |
| node | object | `{"affinity":null,"nodeSelector":null,"tolerations":null}` | Allows to install the nodeplugin on a specific node or node group |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)
