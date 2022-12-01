https://kubernetes.io/docs/tutorials/kubernetes-basics/
https://learnk8s.io/deploying-nodejs-kubernetes
# kuburnetes

automate containers in cloud

example each contianer a instrument in orchestra 
cunducter to manage musicans cunducter is kuburnetes

k8s cluster services
cluster feeded config.

worker: container host




## Advantages:
- language independant
- smaller teams
- fault isolation
- scalable

## disadv
- complex spaghetti of microservices aka compexlity

vocab
- kubelet application that runs and communicate with master node and run pods
- pods runs containers inside it exist on node
- service handle Requests how they routeted and handled. Usually a load balancer
- kubectl command line tool
- minikube local hosted k8


# articel

cluster of computer  conneted to work as a single unit. abastraction allow to deploy container ta cluster without tying to single machine. packaged in a way that decouples them. automates distrub and scheduling of application


control plane : coordinate cluster
node: are the workes that run applications

control-plane manages cluster: scheduling maintaining scaling and updates
node: vm or pc that serves worker machines in cluster. got kublete that manges the node nad communicate with the control panel. 

deploying: tell controlplane start applicaiton containers run on cluster nodes. node communicate with controlplane using kubernetes api. Use directly aswell interacting with cluster. deploy with config that instructs how to creat and update. 


services:

    when node dies the pods running on the node are lost. when node dies pods are lost. Replica set drive cluster back to state.
    service defined with yaml set of pads target detmined by label selector 

    each pod unique ip but not exposed outside cluster service fixes that.
    - CLusterIP expose on internal ip. On by default service only reacable within cluster
    - nodeport exposes the service of each node in cluster accisble with ip:port from outside
    - Loadbalancer subset of node port spread over selected projects
    - external name setup with CNAME aka domain 
    routes routes traffic to pods and let pods die and replicate without impacting application. pods that depends on each other gets routed handled by kubernetes. 

    match a set of pods using labvels and selectors. label/kes attached to pods and used for version dev/test/prod embed version tags. Used for good cli and ui interaction

    label example:
        metadata:
        name: label-demo
        labels:
            environment: production
            app: nginx

    5 scaleing 
        increase amount of pods and load balance send to available pods 
    







































