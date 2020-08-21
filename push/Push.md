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

[1] A private container registry with scanning capabilities and role-based access control offers leverage on security, governance, and management efficiency.

[2] You do not have much control over the images stored in an external registry. New images could be added and already existing images could be removed from the registry at any time. For example, most registries of framework providers do not preserve all images they publish for a long time. 

This is also applicable to product Docker images available at [WSO2 Private Docker Registry](https://docker.wso2.com) mainly due to limitations of storage. For each product version, new images are being frequently added with the latest [WSO2 Updates](https://wso2.com/updates) to products and changes to docker resources used. With limitations of storage, not all images being pushed could be retained in the registry for a long time.

As a result, WSO2 best advise the use of your own private container registry to host all the required images in your deployments, so that you have full control over them. In a rollback event, the recovery of previous version images is effortless with zero risks and zero dependence on outside sources.
