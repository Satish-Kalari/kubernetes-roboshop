Once eks cluster is created, we can use kubectl to interact with the cluster. 

access workstation via supper putty

# kubens configuration installation (https://github.com/ahmetb/kubectx)
in home directory of workstation
    sudo git clone https://github.com/ahmetb/kubectx /opt/kubectx
    sudo ln -s /opt/kubectx/kubens /usr/local/bin/kubens

then cd kubernetes-roboshop/catalogue
    kubens roboshop #this will set roboshop namespace as default, so every time we need not to give -n roboshop
    example: kubectl get pods instead of kubectl get pods -n roboshop
 

docker build -t satishkalari/mongodb:v1 .
docker login
docker push satishkalari/mongodb:v1

kubectl apply -f manifest.yaml
kubectl create deployment mongodb --image=satishkalari/mongodb:v1


# command to see if one pad is connection with other pod
kubectl exec -it <pod-name> -n <namespace> -- sh 
    once kubens is set to roboshop, we need not to give -n roboshop
    then kubectl exec -it <pod-name> -- sh

# command to see pod logs
kubectl logs <pod-name> -n <namespace> 
    once kubens is set to roboshop, we need not to give -n roboshop
    then kubectl logs <pod-name>

commans to see services
kubectl get svc




# apiVersion: apps/v1 vs apiVersion: v1
    apiVersion: apps/v1 is used for deployment, statefulset, daemonset
    apiVersion: v1 is used for service, pod, namespace, configmap, secret, persistentvolume, persistentvolumeclaim, resourcequota, limitrange, replicationcontroller, poddisruptionbudget, priorityclass, serviceaccount, customresourcedefinition, podpreset, podsecuritypolicy


# difference between kubectx and kubens
    kubectx is used to switch between different kubernetes cluster
    kubens is used to switch between different namespace in the same cluster
