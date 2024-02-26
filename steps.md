Once eks cluter is created, we can use kubectl to interact with the cluster. 

access worksation via supper putty


docker build -t satishkalari/monodb:v1 .
docker login
docker push satishkalari/monodb:v1

kubectl apply -f manifest.yaml
kubectl create deployment mongodb --image=satishkalari/monodb:v1


