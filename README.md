# kubernets

Install Kubernetes on master and 3 nodes:
Go step by step and you can install master and nodes for kubernets 

=> https://severalnines.com/blog/installing-kubernetes-cluster-minions-centos7-manage-pods-services

Install cockepit for visual 
=> https://www.youtube.com/watch?v=QX8Lxa2KnL0


kubectl create -f ./resources/pod.yaml 
kubectl create -f ./resources/pod2.yaml 

at this point if you get error like this:
Error from server (ServerTimeout): error when creating "pod.yaml": No API token found for service account "default", retry after the token is automatically created and added to the service account
 => modified /etc/kubernetes/apiserver file (Disable this line)
 #KUBE_ADMISSION_CONTROL="--admission-control=NamespaceLifecycle,NamespaceExists,LimitRanger,SecurityContextDeny,ServiceAccount,ResourceQuota"
  run restart.sh ( restart the services)
  
kubectl get pod nginx
kubectl get pod centos

kubectl delete pod nginx
kubectl delete pod centos


ReplicaSet 
kubectl create -f ./resources/replicaset.yaml
kubectl get replicaset demo
kubectl get pods
kubectl scale --replicas=7 replicaset/demo
kubectl scale --replicas=4 replicaset/demo

kubectl delete pod demo-bclkr (when you delete pod from replicaset it automatic create a new pod to maintain the replicaset number consistnce)
                            like if I delete 1 pod from the replicas=4 it creates a new pod in that cluster to mainain replicas=4)
kubectl delete replicaset demo

(limitation of replicaset is you cant change the conatiners templete)


Deployment:
Apllivation lifecyle

