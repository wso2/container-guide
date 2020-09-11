# 2. Pushing your image to a container registry

This chapter describes why it is important to push your image to a container registry.

### Contents

The following will be discussed in detail in the document.

* [2.1. Why should you have your own private registry ?](#hhy-private-registry)
* [2.2. How to secure your private registry ?](#how-to-secure)
* [2.3. Scanning and Auditing](#scanning-auditing)

<br/>

## <a name="why-private-registry"></a>2.1. Why should you have your own private registry ?

This is essential due to a couple of reasons:

[1] A private container registry with scanning capabilities and role-based access control offers leverage on security, governance, and management efficiency.

[2] You do not have much control over the images stored in an external registry. New images could be added and already existing images could be removed from the registry at any time. For example, most registries of framework providers do not preserve all images they publish for a long time. 

This is also applicable to product Docker images available at [WSO2 Private Docker Registry](https://docker.wso2.com) mainly due to limitations of storage. For each product version, new images are being frequently added with the latest [WSO2 Updates](https://wso2.com/updates) to products and changes to docker resources used. With limitations of storage, not all images being pushed could be retained in the registry for a long time.

As a result, WSO2 best advise the use of your own private container registry to host all the required images in your deployments, so that you have full control over them. In a rollback event, the recovery of previous version images is effortless with zero risks and zero dependence on outside sources.

## <a name="how-to-secure"></a>2.2. How to secure your private registry ?

Your private registry is the place where you host all the images required for your deployment. When you push an image to the registry, it is always important to be sure that you push the exact image that you want to store in your registry. When you pull an image from the registry, it is also important to be sure that you pull the exact image that you want to retrieve from your registry. Since the transfer of data in both of these situations happens in HTTP, to avoid any man-in-the-middle attacks, securing the transfer using `SSL security` is essential. 

Secondly to provide access only to authorized personel even with in your organization, it is important that you enable atleast `basic authentication` to secure your registry.  

## <a name="scanning-auditing"></a>2.3. Scanning and Auditing

If an image includes a vulnerability, then every container generated using that image will also include that vulnerability. New images and newer versions of existing images may be pushed frequently into your private registry. Every change carries with it the possibility of introducing a new vulnerability — and all too often, an old vulnerability resulting from the use of an outdated software package.

`Scanning` : You need to schedule regular scans of your repository in order to detect such vulnerabilities. Most of the organizations that maintain major public registries (such as Docker) provide their own scanning services. Even for private registries, there are a plenty of security providers to offer extended scanning capabilities, with key features such as scanning-results alerts, and automatically preventing images that are not trusted from being used.

`Auditing` : You can (and should) go beyond scanning for vulnerabilities by auditing images for age, as well as outdated packages. You can flag older images and those with older dependencies as outdated and schedule them for updating. Adopting a policy of regularly updating and refreshing older images makes it easier to eliminate vulnerabilities which may have gone undetected.