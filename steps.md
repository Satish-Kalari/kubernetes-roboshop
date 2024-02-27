Once eks cluster is created, we can use kubectl to interact with the cluster. 
   - look at kubernetes/ecsctl/Cluster-SettingUp.md for more details to setup cluster

access workstation via supper putty

# create namespace
    kubectl apply -f namespace.yaml

# kubens configuration installation (https://github.com/ahmetb/kubectx)
in home directory of workstation
    sudo git clone https://github.com/ahmetb/kubectx /opt/kubectx
    sudo ln -s /opt/kubectx/kubens /usr/local/bin/kubens

then cd kubernetes-roboshop/catalogue
    kubens roboshop #this will set roboshop namespace as default, so every time we need not to give -n roboshop
    example: kubectl get pods instead of kubectl get pods -n roboshop
 
docker hub login
    sudo docker login
    username: satishkalari
    password: satish123

docker build -t satishkalari/mongodb:v1 .
docker push satishkalari/mongodb:v1

kubectl apply -f manifest.yaml

# to see logs of pod
kubectl logs <pod-name> -n <namespace>, 
    no namespace is required if kubens is set to roboshop

# command to see nodes
kubectl get nodes

# command to see services
kubectl get svc

# command to see pods
kubectl get pods

# command to see deployments
kubectl get deployments

# command to see statefulset
kubectl get statefulset

# command to see daemonset
kubectl get daemonset

# command to see configmap
kubectl get configmap

# command to see secret
kubectl get secret

# command to see persistentvolume
kubectl get persistentvolume

# command to see namespace
kubectl get namespace



# command to see if one pad is connection with other pod
kubectl exec -it <pod-name> -n <namespace> -- sh 
    once kubens is set to roboshop, we need not to give -n roboshop
    then kubectl exec -it <pod-name> -- sh

# command to see pod logs
kubectl logs <pod-name> -n <namespace> 
    once kubens is set to roboshop, we need not to give -n roboshop
    then kubectl logs <pod-name>

# command to delete pod
kubectl delete pod <pod-name> -n <namespace>
    once kubens is set to roboshop, we need not to give -n roboshop
    then kubectl delete pod <pod-name>

***once pad is deleted git pull updated code and apply the manifest file again then if we delete the pod, it will create new pod with updated code***


# apiVersion: apps/v1 vs apiVersion: v1
    apiVersion: apps/v1 is used for deployment, statefulset, daemonset
    apiVersion: v1 is used for service, pod, namespace, configmap, secret, persistentvolume, persistentvolumeclaim, resourcequota, limitrange, replicationcontroller, poddisruptionbudget, priorityclass, serviceaccount, customresourcedefinition, podpreset, podsecuritypolicy


# difference between kubectx and kubens
    kubectx is used to switch between different kubernetes cluster
    kubens is used to switch between different namespace in the same cluster
