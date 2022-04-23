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
git commit -m 'initial gh page'
git push --set-upstream origin gh-pages
check that github pages is enabled from the settngs on the repo
example: https://github.com/Harphies/harphies-apps-helm-charts/settings/pages
The site is published at this url: https://harphies.github.io/harphies-apps-helm-charts/
```

## Relase the Chart with Helm Chart Releaser or helm commands

Using the combination of helm package and helm repo  or helm chart releaser

```
git checkout main
helm lint charts/*
helm package charts/{harphies-app,prototype-app} --destination .deploy || helm package charts/* --destination .deploy 

```

## Create the Helm Chart Repository Index

```
git checkout gh-pages
helm repo index --url https://harphies.github.io/harphies-apps-helm-charts/ .
cat index.yaml 
```

## Publish charts to Repo with Helm chart Releaser

```
$ brew tap helm/tap
$ brew install chart-releaser
```