# NKP Hello World Demo App

This app is used to demonstrate how to add an app to NKP Application Catalog.

## Instructions
Before following the instructions in the links below, create a Kubernetes secret on your cluster for Docker Hub so you do not reach the rate limit. The secret will be used to pull the image from Docker Hub.

Command to run: 
```
kubectl create secret docker-registry dockerhub-secret \
  --docker-server=https://index.docker.io/v1/ \
  --docker-username=<your-username> \
  --docker-password=<your-password> \
  --docker-email=<your-email>
```

I have followed the following guide to create app and add to NKP Application Catalog:
- Create customer app: [LINK](https://www.nutanix.dev/2026/01/07/creating-custom-applications-for-nkp-part-1/)
