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
- Part 1 - Create custom app: [LINK](https://www.nutanix.dev/2026/01/07/creating-custom-applications-for-nkp-part-1/)
- Part 2 - Create custom app for NKP: [LINK](https://www.nutanix.dev/2026/01/14/creating-custom-applications-for-nkp-part-2/)
- Part 3 - Add custom app to NKP Application Catalog: [LINK](https://www.nutanix.dev/2026/01/21/creating-custom-applications-for-nkp-part-3/) 

For Part 3, I pushed the chart to GitHub Container Registry. These are the steps I followed: 
```
# Log in to GHCR, use a Personal Access Token (PAT) for the password. 
helm registry login ghcr.io

# Push the chart to GHCR
helm push hello-nkp-0.1.0.tgz oci://ghcr.io/<github-username-or-org>/helm-charts

# Example: 
helm push hello-nkp-0.1.0.tgz oci://ghcr.io/pauldjmetsi/helm-charts
helm push hello-nkp-0.2.0.tgz oci://ghcr.io/pauldjmetsi/helm-charts

# To reference the chat 
oci://ghcr.io/<github-username-or-org>/helm-charts/hello-nkp
```

Example command to add the app to NKP Application Catalog:
```
nkp create catalog-application --url oci://ghcr.io/pauldjmetsi/nkp-apps/hello-world --tag 0.1.0 --workspace kommander-workspace
```

# Notes 
Validate catalog-application:
```

```