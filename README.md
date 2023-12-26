# Volumez-CSI

## Usage
[Helm](https://helm.sh) must be installed to use the charts.  Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:
```bash
helm repo add volumez-csi https://volumeztech.github.io/helm-csi
 ```

### Install

To install the volumez-csi chart:
```bash
helm install my-volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver --create-namespace --dependency-update
```

### Install Only on Specific Node/Node-Group
To install the volumez-csi on specific node or nodegroup, label the node/nodegroup and add the following to the end of install command (fill in the correct values in <>):
```bash
--set-json 'csiNodeVlzplugin.affinity={"nodeAffinity":{"requiredDuringSchedulingIgnoredDuringExecution":{"nodeSelectorTerms":[{"matchExpressions":[{"key":<label-key>,"operator":"In","values":[<label-values]}]}]}}}```

### Upgrade

If you had already added this repo earlier, run `helm repo update` to retrieve the latest versions of the packages. 
You can then run `helm search repo volumez-csi` to see the charts.<br/>
To upgrade the chart:
  ```bash
  helm upgrade my-volumez-csi . -n vlz-csi-driver --set certmanager.installCRDs=false
  ```

### Uninstall

To uninstall the chart:
```bash
helm uninstall my-volumez-csi
```
