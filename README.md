# Volumez-CSI

## Usage

[Helm](https://helm.sh) must be installed to use the charts. Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

```bash
helm repo add volumez-csi https://volumeztech.github.io/helm-csi --force-update
```

### Configuration

The chart supports the following key configuration options:

#### Required Configuration
- `vlzAuthToken`: Volumez authentication token (refresh token)

For detailed configuration options, please refer to the [volumez-csi chart README](./charts/volumez-csi/README.md).

### Install

To install the `volumez-csi` chart:

```bash
helm install volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver --create-namespace \
  --set vlzAuthToken="your-auth-token" 
```

To install a specific chart version:
```bash
helm install volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver --create-namespace \
  --set vlzAuthToken="your-auth-token" \
  --version VERSION_TAG
```

Example with specific version:
```bash
helm install volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver --create-namespace \
  --set vlzAuthToken="your-auth-token" \
  --version 1.31.0-rc.1
```

#### Node-Specific Installation

To install `volumez-csi` on specific nodes or node groups, first label the node(s) appropriately.
Then, add the following flag to your helm install command, replacing `<label-key>` and `<label-values>` with your actual labels:

```bash
--set-json 'node.affinity={"nodeAffinity":{"requiredDuringSchedulingIgnoredDuringExecution":{"nodeSelectorTerms":[{"matchExpressions":[{"key":"<label-key>","operator":"In","values":["<label-values>"]}]}]}}}'
```

Example - schedule only on nodes labeled with `nodepool-type=app` or `nodepool-type=media`:
```bash
helm install volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver --create-namespace \
  --set vlzAuthToken="your-auth-token" \
  --set-json 'node.affinity={"nodeAffinity":{"requiredDuringSchedulingIgnoredDuringExecution":{"nodeSelectorTerms":[{"matchExpressions":[{"key":"nodepool-type","operator":"In","values":["app", "media"]}]}]}}}'
```

### Upgrade

If you previously added this repository, run `helm repo update` to fetch the latest package versions.
Afterwards, you can run `helm search repo volumez-csi -l` to view the available charts.

To upgrade the chart:
```bash
helm upgrade volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver
```

To upgrade to a specific chart version:
```bash
helm upgrade volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver --version VERSION_TAG
```

Example:
```bash
helm upgrade volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver --version 1.31.0-rc.1
```

### Uninstall

To uninstall the chart:

```bash
helm uninstall volumez-csi -n vlz-csi-driver
```
