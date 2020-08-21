# 4. Persisting and Sharing

This chapter depicts important information about runtime artifact storage of an existing WSO2 product deployment in a container platform.

## Contents

The following will be discussed in detail in the document.

* [4.1. Why do we need to store?](#why-do-we-need-to-store?)
* [4.2. Recommended storage options for WSO2 products](#recommended-storage-options-for-wso2-products)

### Why do we need to store?

In the context of WSO2 product deployment, the need for storage of artifacts arises due to the following reasons:

* Persist created runtime artifacts

* Share created runtime artifacts across multiple instances in deployments with high availability support

> For example, in WSO2 API Manager production deployment patterns, it is recommended to use a suitable storage option
  for the aforementioned purposes.
>
> Following are some such scenarios.
>
>   - Persist Apache Solr-based indexed data in every Publisher and DevPortal profile instance, individually
>
>   - Persist and share API runtime artifacts (created in `<APIM_HOME>/repository/deployment/server/synapse-configs`) directory
>     across multiple instances of the API Manager Gateway profile
>
> For advanced details on persistent runtime artifacts of WSO2 API Manager, please refer to the official
[documentation](https://apim.docs.wso2.com/en/latest/install-and-setup/setup/reference/common-runtime-and-configuration-artifacts/#persistent-runtime-artifacts).

### Recommended storage options for WSO2 products

As highlighted in the [previous](#why-do-we-need-to-store?) section, there are numerous use cases which instigate the need
for storage in WSO2 product deployments.

WSO2 recommends using the most suitable persistent storage solution depending on the scenario.

* Persist runtime artifacts of a single instance: 

  For this purpose, you may use any persistent storage solution supporting either `ReadWriteOnce` or `ReadWriteMany`
  [access modes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes).

* Persist and share runtime artifacts runtime artifacts across multiple instances of a product profile

  For this purpose, you may use any persistent storage solution supporting `ReadWriteMany`
  [access mode](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes).

The following is a list of storage options using with production grade WSO2 product deployments in Kubernetes environments that
have been tested along with the corresponding [Kubernetes StorageClasses](https://kubernetes.io/docs/concepts/storage/storage-classes/).

* Network File System (NFS)

  - WSO2 product Helm charts use the stable [NFS Server Provisioner](https://hub.helm.sh/charts/stable/nfs-server-provisioner)
    to render a NFS server, for the purpose of evaluation.
    
  - WSO2 product deployments have been tried and tested with NFS based solutions like [Google FileStore](https://cloud.google.com/filestore)
    (please refer to instructions for [WSO2 API Manager](https://github.com/wso2/kubernetes-apim/issues/359#issuecomment-639729986) and
    [Identity Server](https://github.com/wso2/kubernetes-is/issues/227#issuecomment-639735208)).

* Ceph File System (CephFS)

  - WSO2 product deployments have been tested with [CephFS cluster deployed using the Rook Operator version `1.3`](https://rook.io/docs/rook/v1.3/ceph-quickstart.html).
    (please refer to instructions for [API Manager](https://github.com/wso2/kubernetes-apim/issues/410#issuecomment-654070688) and
    [Identity Server](https://github.com/wso2/kubernetes-is/issues/240#issuecomment-654681300)).
