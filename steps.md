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





kubectx # to see all the context
kubens # to see all the namespace
