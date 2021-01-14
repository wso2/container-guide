# 3. Deploying into production

This chapter depicts important information about deploying your images into production.

### Contents

The following will be discussed in detail in the document.

* [3.1. Why do you need a container orchestrator ?]
* [3.2. Why should you choose Kubernetes ?]
* [3.3. Kubernetes Vs. OpenShift ?]

<br/>

## 3.1. Why do you need a container orchestrator ?

Even though it is easy to manage, maintain, and run all your containers in a single node cluster this practice would lead to a single point of failure (if the node suddenly malfunctions due to some problems). As a result, it’s always advisable to divide your containers into two or more nodes in a cluster. However, depending on the load we not only have to increase the number of containers we manage, but we will also have to increase the number of nodes we manage for the cluster. Conversely, the higher the number of containers and nodes, the effort and complexity of managing the cluster increase in high proportions. Doing this manually is a daunting task and is highly error prone. 

This is where a container orchestration platform comes handy as a solution to the problem. It can manage all the bare metal machines and virtual machines on which you need to run your containers. Furthermore, it could also manage your containers by launching them on the underlying machines, making sure they are distributed, and keeping them healthy.

<br/>

## 3.2. Why should you choose Kubernetes ?

When it comes to the three leading container orchestration platforms, i.e., Mesos, Kubernetes, and Docker Swarm, Kubernetes is the undisputed leader due to the following reasons:

* Wide adoption
* Proven, battle-tested solution
* Open source
* High Availability
* Scalability
* Portability
* Powerful and easy-to-use features

<br/>

<img src="../imgs/deploy/kubernetes-adoption.png" width="900">

<br/>

With its wide adoption and powerful, easy-to-use features, we at WSO2 believe that it can soon become the defacto container orchestration platform standard in the world. It is for this reason that we continue to provide development support for Kubernetes-based container deployments of our products (as we have done for more than two years).
