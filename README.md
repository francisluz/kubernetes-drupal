# kubernetes-drupal
Script to create the drupal site on Kubernetes and Google Container Engine


# Script to create Drupal container single Pod

hello-drupal

gcloud beta container clusters create hello-drupal \
    --num-nodes 1 \
    --machine-type g1-small

gcloud compute instances list

kubectl run drupal --image=wadmiraal/drupal --port=80

kubectl expose rc drupal --create-external-load-balancer=true

kubectl get services drupal

kubectl get nodes


# GET NODE NAME PREFIX ABOVE

Change the XXXXXX from your prefix name

gcloud compute firewall-rules create hello-drupal-80 --allow tcp:80 \
    --target-tags gke-hello-drupal-XXXXXX-node

kubectl get services drupal

GET EXTERNAL IP ADDRESS

# CLEANUP

kubectl delete services drupal

gcloud beta container clusters delete hello-drupal

gcloud compute firewall-rules delete hello-drupal-80
