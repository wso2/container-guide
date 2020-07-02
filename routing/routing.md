# Routing

This document depicts important information about configuring routing for an existing WSO2 product deployment in a
 container platform.
 
The following will be discussed in detail in the document.

* [Exposing your application to outside](#exposing-your-application-to-outside )
* [Configuring hostname](#configuring-hostname)
* [DNS mapping](#dns-mapping)
* [Configuring SSL](#configuring-ssl)
* [Tips on Session Affinity](#tips-on-session-affinity)

### Exposing your application to outside

We recommend the use of [official WSO2 product Helm Charts](https://hub.helm.sh/charts/wso2) for production grade WSO2 
product deployments in Kubernetes environments. [Kubernetes Ingress resources](https://kubernetes.io/docs/concepts/services-networking/ingress/)
are used to expose expose WSO2 product services to outside of the Kubernetes environment.

Kubernetes Ingress resources are capable of determining traffic based on the host and path forwarded to them by
backends. It also operates on the application layer of the network stack (HTTP) and can provide features like cookie-based
session affinity and SSL terminations. 

>WSO2 recommend [Community NGINX](https://kubernetes.github.io/ingress-nginx/) as the Ingress controller for production 
>grade product deployments in Kubernetes environments.

### Configuring hostname

For each WSO2 product that is exposed via the Ingress, must have a hostname. The hostname should be configured for
each Ingress resource and for each WSO2 product configuration.

### DNS mapping

In order to access the services that are exposed through the Ingress controller, it is required to add DNS mappings
 where each configured host name should be resolved to the Load balancer that fronts the Ingress controller. For
testing purposes, it is possible to add host name mapping entries to the hosts file in the Operating system(For
 example, Ubuntu: /etc/hosts).
 
### Configuring SSL

It is recommended to do SSL termination at Load balancer in this case at Ingress controller. With this method, it is
possible to manage production certificates for the entire Kubernetes cluster in a single location, the Ingress
controller.

With in the Kubernetes environment, WSO2 products use HTTPS with self-signed certificates for communication. 

There are two ways of configuring SSL termination for Ingress controller.

1. Use a wild card certificate as the default certificate
    * In this approach, all the services that are exposed should be configured with a host name within the wild card
     domain  
1. Configure individual certificates for each host name
    * In this approach, it is possible to have different host names for each exposed services where each Ingress is
     configured with a certificate for a particular host name
     
### Tips on Session Affinity

Some of the WSO2 products require to maintain the session of end user across subsequent HTTP calls. In a Kubernetes
environment, **Session Affinity**  must be configured at Ingress resources. In **NGINX** ingress controller, **Cookie**
based session affinity is used as the default.  
