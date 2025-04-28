# Volumez-CSI

## Usage

[Helm](https://helm.sh) must be installed to use the charts. Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

```bash
helm repo add volumez-csi https://volumeztech.github.io/helm-csi --force-update
```

### Configuration

For detailed configuration options, please refer to the [volumez-csi chart README](./charts/volumez-csi/README.md).

### Install

To install the `volumez-csi` chart:

```bash
helm install volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver --create-namespace 
```

To install a specific chart version:
```bash
helm install volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver --create-namespace --version VERSION_TAG
```
i.e:
```bash
helm install volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver --create-namespace --version 1.31.0-rc.1
```
<br/>

To install `volumez-csi` on a specific node or node group, first label the node(s) appropriately.
Then, add the following flag to the end of your helm install command, replacing `<label-key>` and `<label-values>` with your actual labels:

```bash
--set-json 'csiNodeVlzplugin.affinity={"nodeAffinity":{"requiredDuringSchedulingIgnoredDuringExecution":{"nodeSelectorTerms":[{"matchExpressions":[{"key":"<label-key>","operator":"In","values":["<label-values>"]}]}]}}}'
```

i.e:
To schedule the driver only on nodes labeled with nodepool-type=app or nodepool-type=media, use:
```bash
--set-json 'csiNodeVlzplugin.affinity={"nodeAffinity":{"requiredDuringSchedulingIgnoredDuringExecution":{"nodeSelectorTerms":[{"matchExpressions":[{"key":"nodepool-type","operator":"In","values":["app", "media"]}]}]}}}'
```

### Upgrade

If you previously added this repository, run `helm repo update` to fetch the latest package versions.
Afterwards, you can run `helm search repo volumez-csi -l` to view the available charts.<br/>
To upgrade the chart:
  ```bash
  helm upgrade volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver 
  ```

To upgrade to a specific chart version:
  ```bash
  helm upgrade volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver --version VERSION_TAG
  ```
i.e:
  ```bash
  helm upgrade volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver --version 1.31.0-rc.1
  ```

### Uninstall

To uninstall the chart:

```bash
helm uninstall volumez-csi -n vlz-csi-driver
```
