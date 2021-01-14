<img src="imgs/wso2.jpg" width="250">

# Running WSO2 Products on Containerization Platforms
The Guide of Best Practices and Recommendations

## Table of Contents
- ### [1. Building a container image](./build/Building.md)
    * [1.1. Why should you choose Docker as your container runtime ?](./build/Building.md#why-docker)
    * [1.2. Using WSO2 images](./build/Building.md#using-wso2-images)
    * [1.3. Building from source](./build/Building.md#building-from-source)
    * [1.4. Tips to harden your image](./build/Building.md#tips-to-harden-your-image)
    * [1.5. Tips on Tagging](./build/Building.md#tips-on-tagging)
    * [1.6. Vulnerability scanning and container security check](./build/Building.md#scanning)
    * [1.7. Image signing and Verification](./build/Building.md#signing)

- ### [2. Pushing your image to a container registry](./push/Pushing.md)
    * [2.1. Why should you have your own private registry ?](./push/Pushing.md#why-private-registry)
    * [2.2. How to secure your private registry ?](./push/Pushing.md#how-to-secure)
    * [2.3. Scanning and Auditing](./push/Pushing.md#scanning-auditing) 

- ### [3. Deploying into production](./deploy/Deploying.md)
    * [3.1. Why do you need a container orchestrator ?](./deploy/Deploying.md)
    * [3.2. Why should you choose Kubernetes ?](./deploy/Deploying.md)
    * [3.3. Kubernetes Vs. OpenShift ?](./deploy/Deploying.md)
    * [3.4. Helm as package manager](./deploy/Deploying.md) 
    * [3.5. Supporting Infrastructure](./deploy/Deploying.md)
    * [3.6. Resource Allocation](./deploy/Deploying.md)
    * [3.7. Deployment definition tips](./deploy/Deploying.md) 
    * [3.8. Managing configurations](./deploy/Deploying.md)  
    * [3.9. Managing keystores, certificates and other artifacts](./deploy/Managing_Keystores_And_Truststores.md)
    * [3.10. Managing databases](./deploy/Deploying.md)
    * [3.11. Production deployment tips](./deploy/Deploying.md)
    * [3.12. Managing security](./deploy/Deploying.md)

- ### [4. Storage](./store/Persisting_And_Sharing.md)
    * [4.1. Why do we need storage for WSO2 products ?](./store/Persisting_And_Sharing.md#why-do-we-need-to-store?)
    * [4.2. Recommended storage options for WSO2 products](./store/Persisting_And_Sharing.md#recommended-storage-options-for-wso2-products)
    * [4.3. Storage binding tips](./store/Persisting_And_Sharing.md)
    * [4.4. Storage type and size](./store/Persisting_And_Sharing.md)

- ### [5. Routing](./route/Routing.md)
    * [5.1. Exposing your application to outside](./route/Routing.md#exposing-your-application-to-outside)
    * [5.2. Configuring hostnames](./route/Routing.md#configuring-hostname)
    * [5.3. Configuring SSL](./route/Routing.md#configuring-ssl)
    * [5.4. DNS mapping](./route/Routing.md#dns-mapping)
    * [5.5. Tips on Session Affinity](./route/Routing.md#tips-on-session-affinity)

- ### [6. Scaling your deployment](./scale/Scaling_Deployments.md)
    * [6.1. What is scaling ?](./scale/Scaling_Deployments.md#what-is-scaling?)
    * [6.2. When do we need to scale ?](./scale/Scaling_Deployments.md#when-do-we-need-to-scale?)
    * [6.3. Scaling metrics](./scale/Scaling_Deployments.md#scaling-metrics)
    * [6.4. Scaling WSO2 product profiles](./scale/Scaling_Deployments.md#scaling-wso2-product-profiles)
    * [6.5. Scaling strategies](./scale/Scaling_Deployments.md#scaling-strategies)

- ### [7. Propagating Updates](./update/Propagating_Updates.md)
    * [7.1. When do we need to update ?](./update/Propagating_Updates.md#when-do-we-need-to-update?)
    * [7.2. Simplest way to perform an update](./update/Propagating_Updates.md#simplest-way-to-perform-an-update)
    * [7.3. Achieve zero downtime](./update/Propagating_Updates.md#achieve-zero-downtime)

- ### [8. Publishing Logs](https://github.com/wso2/container-guide)
    * [8.1. Why do we need centralized logging ?](https://github.com/wso2/container-guide)
    * [8.2. Centralized logging with EFK](https://github.com/wso2/container-guide)
    * [8.3. Logging storage and Backup](https://github.com/wso2/container-guide)  

- ### [9. Monitoring and Alerting](https://github.com/wso2/container-guide)
    * [9.1. Why do we need metrics monitoring](https://github.com/wso2/container-guide)
    * [9.2. Metrics monitoring with Prometheus and Kibana](https://github.com/wso2/container-guide)
    * [9.3. Prometheus operator and exporters](https://github.com/wso2/container-guide)
    * [9.4. Alertmanager Integration with Prometheus](https://github.com/wso2/container-guide)
    * [9.5. Monitoring storage and Backup](https://github.com/wso2/container-guide)

- ### [10. Development and Testing](https://github.com/wso2/container-guide)
    * [10.1. Planning your non-production environments](https://github.com/wso2/container-guide)
    * [10.2. Kubernetes Vs. Openshift way of execution](https://github.com/wso2/container-guide)

- ### [11. Maintenance](https://github.com/wso2/container-guide)
    * [11.1. Importance of CI/CD](https://github.com/wso2/container-guide)
    * [11.2. WSO2 Kubernetes Pipeline](https://github.com/wso2/container-guide)

- ### [12. A deployment checklist in summary](https://github.com/wso2/container-guide)
    * [12.1. Building a container image](https://github.com/wso2/container-guide)
    * [12.2. Pushing your image to a container registry](https://github.com/wso2/container-guide)
    * [12.3. Deploying into production](https://github.com/wso2/container-guide)
    * [12.4. Scaling your deployment](https://github.com/wso2/container-guide)
    * [12.5. Propagating updates](https://github.com/wso2/container-guide)
    * [12.6. Publishing and analysing logs](https://github.com/wso2/container-guide)
    * [12.7. Monitoring and Alerting](https://github.com/wso2/container-guide)
    * [12.8. Disaster Recovery](https://github.com/wso2/container-guide)
    * [12.9. Development and Testing](https://github.com/wso2/container-guide)
    * [12.10. Maintenance](https://github.com/wso2/container-guide)

- ### [13. Appendix](https://github.com/wso2/container-guide)