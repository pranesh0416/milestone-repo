# milestone-repo

this is the app which helps in deploying a voter app

the app uses mongo db for database
then goline api for communication
finally react for frontend

we create a eks cluster with the specified roles
AmazonEKSBlockStoragePolicy
AmazonEKSClusterPolicy
AmazonEKSComputePolicy
AmazonEKSLoadBalancingPolicy
AmazonEKSNetworkingPolicy

we create a nodegroup with the available instance types for the pods to run smoothly
AmazonEBSCSIDriverPolicy
AmazonEC2ContainerRegistryReadOnly
AmazonEKS_CNI_Policy
AmazonEKSWorkerNodePolicy
ElasticLoadBalancingFullAccess


then create a ec2 instance with the specified role which a custom config policy eksaceess and  AmazonEBSCSIDriverPolicy  

upon creating a cluster we create access for the ec2 instance to access the nodes in the cluster
for that we primarily use the ec2 instance role and clusteradmin policy

then in the addons we create a pod identity and then we create ebs csi driver policy addon
which helps in creating the persisent volume
we create a automatic role for on using the pod identity and finally create the add on

then we launch the ec2 instance
install kubectl and aws which helps in communicating with the database

then we config the eks so update so that we can specify the cluster and the region where it is present

then we can fetch the nodes using get nodes the nodes are created and they are up and running

we install the git and import the repo set the workspace

start by deploy the mango stateful set which containes the database and creates persisent volumes

further we set the pod 0 as primary and pod 1 and 2 as secondary only come to work if there is any issue in pod0
then we add the database for the votes
further we create the service for mongo to expose using cluster ip


we deploy the api deployment 
later the api service using load balancer
we can access it and check the database

later edit the value in frontend deployment with the api load balancer for it to run smoothly

finally we deploy the frontend deploy
then the frontend service using loadbalancer
we can see the application add votes and using the instance we can check whether the votes are updated or not

using helm we can install prometheus and grafana as a monitoring service 
run using the loadbalancer and check the metrics

