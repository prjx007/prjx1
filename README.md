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



