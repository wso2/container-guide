# Scaling Deployments

This chapter depicts important information about scaling an existing WSO2 product deployment in a container platform.

## Contents

The following will be discussed in detail in the document.

* [What is scaling?](#what-is-scaling?)
* [When do we need to scale?](#when-do-we-need-to-scale?)
* [Scaling metrics](#scaling-metrics)
* [Scaling WSO2 product profiles](#scaling-wso2-product-profiles)
* [Scaling strategies](#scaling-strategies)

### What is scaling?

In the context of a WSO2 product deployment, assuming that you have provided sufficient computing resources,
scaling refers to increasing/decreasing the number of replicas of a given product profile.

### When do we need to scale?

Following events may instigate scaling of an existing WSO2 product profile.

* The current throughput per second (TPS) handled by the system surpasses a defined threshold TPS that can be handled
  via the available instances.

* The current throughput per second (TPS) handled by the system decreases below a defined threshold TPS that can be handled
  via the available instances.

### Scaling metrics

Thus, TPS handled by an instance of a particular product profile can be considered the primary metric considered for scaling.

Also, secondary metrics such as CPU usage and memory usage of a given product profile instance can be considered.

### Scaling strategies

* Scaling based on CPU

  WSO2 recommends auto scaling of profile instances to be configured with the average CPU threshold between 80%-90%.
  
* Scaling based on memory

  WSO2 recommends auto scaling of profile instances to be configured with the average memory threshold between 80%-90%.

### Scaling WSO2 product profiles

It has to be noted that scalability differ based on the WSO2 product profile. The following highlight such noteworthy cases.

* Scaling API Manager product profiles

  Please refer to scaling recommendations for WSO2 API Manager product profiles defined
  [here](https://apim.docs.wso2.com/en/latest/learn/api-gateway/scaling-the-gateway/).

* Stream Processor based deployments

  A minimum high availability deployment of Stream Processor based deployment is not scalable more than 2 replicas.
  Please see official [documentation](https://docs.wso2.com/display/SP440/Minimum+High+Availability+Deployment)
  for advanced details about this.
