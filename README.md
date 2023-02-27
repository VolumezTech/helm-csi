## Usage

[Helm](https://helm.sh) must be installed to use the charts.  Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

    helm repo add volumez-csi https://volumeztech.github.io/helm-csi

If you had already added this repo earlier, run `helm repo update` to retrieve
the latest versions of the packages.  
You can then run `helm search repo volumez-csi` to see the charts.

To install the volumez-csi chart:
    
    helm dependency build && helm install my-volumez-csi volumez-csi/volumez-csi -n vlz-csi-driver --create-namespace 

To uninstall the chart:

    helm delete my-volumez-csi