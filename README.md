[![CircleCI](https://circleci.com/gh/giantswarm/{APP-NAME}-app.svg?style=shield)](https://circleci.com/gh/giantswarm/{APP-NAME}-app)

# Azure Key Vault to Kubernetes App chart

Giant Swarm offers a Azure Key Vault to Kubernetes (akv2k8s) App which can be installed in workload clusters.
Here we define the akv2k8s chart with its templates and default configuration.

**What is this app?**

This app enables usage of secrets defined in Azure Key Vault in a secure way within the pods.  

**Why did we add it?**

We want to enable customers to make use of the Azure services that are compatible with Kubernetes and can enhance security/

**Who can use it?**

All customers running Azure Workload Clusters.

## Installing

There are 3 ways to install this app onto a workload cluster.

1. [Using our web interface](https://docs.giantswarm.io/ui-api/web/app-platform/#installing-an-app)
2. [Using our API](https://docs.giantswarm.io/api/#operation/createClusterAppV5)
3. Directly creating the [App custom resource](https://docs.giantswarm.io/ui-api/management-api/crd/apps.application.giantswarm.io/) on the management cluster.

## Configuring

### values.yaml
**This is an example of a values file you could upload using our web interface.**
```
global:
  env:
    AZURE_TENANT_ID=YOUR_TENANT_ID
    AZURE_CLIENT_ID=YOUR_KEYVAULT_ID
    AZURE_CLIENT_SECRET=YOUR_CLIENT_SECRET

addAzurePodIdentityException: true
```

### Sample App CR and ConfigMap for the management cluster
If you have access to the Kubernetes API on the management cluster, you could create
the App CR and ConfigMap directly.

Here is an example that would install the app to
workload cluster `abc12`:

```
# appCR.yaml

```

```
# user-values-configmap.yaml


```

See our [full reference page on how to configure applications](https://docs.giantswarm.io/app-platform/app-configuration/) for more details.

## Compatibility

This app has been tested to work with the following workload cluster release versions:

* Azure 15.0.0+

## Limitations

Some apps have restrictions on how they can be deployed.
Not following these limitations will most likely result in a broken deployment.

* Azure Key Vault to Kubernetes app requires [Azure AD Pod Identity app](https://github.com/giantswarm/azure-ad-pod-identity-app/) to be deployed first

## Credit

* https://github.com/SparebankenVest/public-helm-charts/tree/master/stable/akv2k8s
* https://akv2k8s.io/
