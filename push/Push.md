# 2. Pushing your image to a container registry

This chapter depicts important information about pushing your image to a container registry.

### Contents

The following will be discussed in detail in the document.

* [2.1. Why should you have your own private registry ?](#Why-private-registry)
* [2.2. How to secure your private registry ?](#how-to-secure)
* [2.3. Scanning and Auditing](#scanning-auditing)

<br/>

## 2.1. Why should you have your own private registry ?

This is essential due to a couple of reasons:

[1] A private container registry with scanning capabilities and role-based access control offers more security, governance and efficient management.

[2] You do not have much control over the images stored in an external registry. New images could be added and already existing images could be removed from the registry at any time. For example, most registries of framework providers do not preserve all images they publish for a long time. 

This is also applicable to product Docker images available at [WSO2 Private Docker Registry](https://docker.wso2.com) mainly due to limitations of storage. For each product version, new images are being frequently added with latest updates (WSO2 Updates) to products and changes to docker resources used. With limitations of storage, not all images being pushed could be retained in the registry for a long time.

As a result, WSO2 recommends the use of your own private container registry to host all the required images in your deployments, so that you have full control over them. Even just in case of a rollback, the recovery of a previous version is easy at any time with zero risk and zero dependence on outside sources.
