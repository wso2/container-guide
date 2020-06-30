# Propagating Updates

This document depicts important information about updating an existing WSO2 product deployment in a container platform.

## Contents

The following will be discussed in detail in the document.

* [When do we need to update?](#when-do-we-need-to-update?)
* [Simplest way to perform an update](#simplest-way-to-perform-an-update)
* [Achieve zero downtime](#achieve-zero-downtime)

### When do we need to update?

The following are some of the scenarios which instigates the need for an update to an existing
WSO2 product deployment in a container platform.

* Be abreast with improvements and bug fixes by including [WSO2 Updates](https://wso2.com/updates)
* A version migration of the used WSO2 product
* Updates to configuration files and non-configuration artifacts (e.g. binaries such as, third-party libraries,
Carbon extensions in the form of OSGi bundles, [Carbon Applications](https://docs.wso2.com/display/Carbon440/Working+with+Carbon+Applications)
or any security related artifacts such as, Java Keystore files)
* Integrate changes to the container image source
* Integrate changes to the container platform installation resources (e.g. Kubernetes resources or Helm Chart source)

### Simplest way to perform an update

We recommend the use of [official WSO2 product Helm Charts](https://hub.helm.sh/charts/wso2) for production grade WSO2 product deployments
in Kubernetes environments.

Hence, the simplest way to perform an update to an existing WSO2 product deployment is to use a [Helm based upgrade](https://helm.sh/docs/helm/helm_upgrade/).

1. Perform the required change(s).

   The following are some of the probable changes.
   
   * An update of [Helm Values](https://helm.sh/docs/chart_template_guide/values_files/) (e.g. update to the container
     image tag)
   * An update to configuration file(s)
   
2. Perform a Helm based upgrade.

   Kubernetes resources for WSO2 products utilize the most update strategy depending on the following factors.
   
   * Involved WSO2 product profile
   * Achieve zero downtime during the update

**Note:**
> If you are not using Helm package manager to deploy WSO2 product Kubernetes resources, you may have to perform the
  update via Kubernetes client commands.
> For example, in order to apply a configuration file change, you may have to recreate the existing ConfigMap corresponding
  the changed file and perform a [Deployment rollout](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#updating-a-deployment).

### Achieve zero downtime

The most popular update strategy utilized by WSO2 product Kubernetes resources is of type,
[rolling update](https://kubernetes.io/docs/tutorials/kubernetes-basics/update/update-intro/). Both resource types
Deployments and [StatefulSets](https://kubernetes.io/docs/tutorials/stateful-application/basic-stateful-set/#rolling-update)
primarily adopt this strategy.

The prime reason for adopting rolling update strategy is its ability to perform an update with zero downtime.

**Notes:**
> Apart from the rolling update strategy, we adopt [`OnDelete`](https://kubernetes.io/docs/tutorials/stateful-application/basic-stateful-set/#on-delete)
for API Manager's Publisher and DevPortal profiles due to [this](https://github.com/wso2/kubernetes-apim/issues/397) issue.

> This strategy involves user's manual intervention. In order to avoid downtime in deployments with high availability,
it is recommended to perform the deletion of the relevant instances sequentially.
