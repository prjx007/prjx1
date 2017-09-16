# MAC

curl https://sdk.cloud.google.com | bash

exec -l $SHELL

gcloud init

gcloud auth login

# list the configurations 

gcloud config configurations list

gcloud config list

gcloud config set project [PROJECT]

gcloud config set compute/zone us-east1-b

# Listing components

gcloud components list

# Installing components 

# install the kubectl

gcloud components install kubectl

# update to latest version

gcloud components update

# --INSTALL ISTIO------

curl -L https://git.io/getIstio | sh -

kubectl api-versions | grep rbac

kubectl apply -f install/kubernetes/istio-auth.yaml

kubectl apply -f install/kubernetes/addons/prometheus.yaml

kubectl apply -f install/kubernetes/addons/grafana.yaml

kubectl apply -f install/kubernetes/addons/servicegraph.yaml

cd google-cloud-sdk

export PATH=$PWD/bin:$PATH

# grafana dashboard

kubectl port-forward $(kubectl get pod -l app=grafana -o jsonpath='{.items[0].metadata.name}') 3000:3000 &

# istio dashboard
http://localhost:3000/dashboard/db/istio-dashboard

# dotviz

kubectl port-forward $(kubectl get pod -l app=servicegraph -o jsonpath='{.items[0].metadata.name}') 8088:8088 &

http://localhost:8088/dotviz

# Jaeger
kubectl apply -f https://raw.githubusercontent.com/jaegertracing/jaeger-kubernetes/master/all-in-one/jaeger-all-in-one-template.yml

# ZIPKIN
kubectl apply -f install/kubernetes/addons/zipkin.yaml

kubectl get svc

kubectl get pods

cd istio-0.1.6





