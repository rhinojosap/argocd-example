# Service APP

Este es el ejemplo de una aplicacion para deplegar a traves de CLI a Openshift

## En este caso los nombres de los archivos indican el orden de ejecucion

<##>-\<k8s Object prefix\>-\<Object Name\>.yml


## Script de creacion de los proyectos de Argo.

```bash

oc apply -f 00-ns-paas-gitops-service.yml
oc apply -f 20-secret-repository-conection-gitlab-infra.yml
oc apply -f 30-appproject-argocd-service.yml
oc apply -f 40-application-argocd-service.yml

```


## Script de eliminacion de los proyectos de Argo.

```bash

oc delete -f 40-application-argocd-service.yml
oc delete -f 30-appproject-argocd-service.yml
oc delete -f 20-secret-repository-conection-gitlab-infra.yml
oc delete -f 00-ns-paas-gitops-service.yml

```


## Objetos residuantes

```bash

oc delete cm -n paas-gitops-service cm-primer-ejemplo

```