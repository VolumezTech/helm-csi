# Volumez-CSI

## Usage

[Helm](https://helm.sh) must be installed to use the charts. Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

```bash
helm repo add volumez-csi https://volumeztech.github.io/helm-csi
```

### Configuration

For detailed configuration options, please refer to the [volumez-csi chart README](./charts/volumez-csi/README.md).

### Install

To install the volumez-csi chart:

```bash
helm install my-volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver --create-namespace 
```

To install a specific chart version:
```bash
helm install my-volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver --create-namespace --version VERSION_TAG
```
i.e:
```bash
helm install my-volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver --create-namespace --version 1.22.0-rc.1
```

To install the volumez-csi on a specific node or node group, label the node/node group and add the following to the end of the install command (fill in the correct values instead of "label-key" and "label-values"):

```bash
--set-json 'csiNodeVlzplugin.affinity={"nodeAffinity":{"requiredDuringSchedulingIgnoredDuringExecution":{"nodeSelectorTerms":[{"matchExpressions":[{"key":"<label-key>","operator":"In","values":["<label-values>"]}]}]}}}'
```

i.e:

```bash
--set-json 'csiNodeVlzplugin.affinity={"nodeAffinity":{"requiredDuringSchedulingIgnoredDuringExecution":{"nodeSelectorTerms":[{"matchExpressions":[{"key":"nodepool-type","operator":"In","values":["app", "media"]}]}]}}}'
```

### Upgrade

If you had already added this repo earlier, run `helm repo update --force` to retrieve the latest versions of the packages. 
You can then run `helm search repo volumez-csi` to see the charts.<br/>
To upgrade the chart:
  ```bash
  helm upgrade my-volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver 
  ```

To upgrade to a specific chart version:
  ```bash
  helm upgrade my-volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver --version VERSION_TAG
  ```
i.e:
  ```bash
  helm upgrade my-volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver --version 1.23.0-rc.1
  ```

### Uninstall

To uninstall the chart:

```bash
helm uninstall my-volumez-csi -n vlz-csi-driver
```
