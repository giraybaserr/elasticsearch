# ElasticSearch Deployment on Kubernetes

This guide provides step-by-step instructions on how to deploy ElasticSearch version 7.10 on your Kubernetes cluster using Helm.

## Prerequisites

Ensure you have the following tools installed and configured:
- Git
- Helm 3
- kubectl, configured to communicate with your Kubernetes cluster

## Deployment Steps

Follow these steps to deploy ElasticSearch on your Kubernetes cluster:

## Create a Namespace for ElasticSearch

   Before deploying ElasticSearch, create a dedicated namespace in your Kubernetes cluster:

   kubectl create namespace "namespace"

## Clone the ElasticSearch Helm Chart Repository

Clone the ElasticSearch Helm chart repository from GitHub and navigate into the cloned directory:

git clone https://github.com/giraybaserr/elasticsearch.git
cd elasticsearch

## Checkout the Desired Version

Switch to the ElasticSearch version 7.10 branch:

git checkout 7.10

## Deploy ElasticSearch with Helm

Use Helm to deploy ElasticSearch into your chosen namespace:

helm install elasticsearch . --namespace "namespace"

## Verify the Deployment

Check that the ElasticSearch pods are up and running in your namespace:

kubectl get pods -n "namespace"

## Access ElasticSearch

To access the ElasticSearch API, set up port forwarding to one of the ElasticSearch pods:

kubectl port-forward service/elasticsearch-master 9200:9200 -n "namespace"

## Cleanup

To delete the ElasticSearch deployment from your cluster:

helm delete elasticsearch -n <namespace>


