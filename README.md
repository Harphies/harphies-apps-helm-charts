# Helm Charts Creation and Publish to Helm Repositories

## Step1: Create the Helm Chart to Package your application
```
helm create harphies-apps
helm 
helm lint
helm package harphies-app
serve the app locally with helm chart meseum
docker run -rm -it \
    -p 8080:8080 \
    -e DEBUG=1 \
    -e STORAGE=local \
    -e STORAGE_LOCAL_ROOTDIR=/charts \
    -v ${pwd}/charts:charts \
    ghcr.io/helm/chartmuseum:v0.14.0
```

## Example Charts to model after

- https://github.com/kubernetes-sigs/aws-efs-csi-driver/tree/master/charts/aws-efs-csi-driver

## Publishing Helm charts to Github Pages as Helm Repo
Enable Github pages branch on the repo hosting the charts
```
git checkout --orphan gh-pages
rm -rf charts
git add . --all
```
