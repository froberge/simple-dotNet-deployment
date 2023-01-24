# Simple DotNet Application Deploy

This repository contains the different manifest needed to deploy the dotNet application build with the [GitHub Action Demo](https://github.com/froberge/ocp-githubaction-demo/tree/working_demo_gitops) to an OpenShift/Kubernetes clusters.


This repository is used to implement the `best pratices` to seperate the code from the deployment manifest.

It is use for demo purposes and can deploy the images created by the GitHub actions pipeline

### Prerequisite

1. Access to github
1. Clone/Fork of this repository
1. Access to an OpenShift Cluster
1. OpenShift CLI
1. OpenShift GitOps operator install on the cluster


### Content

# Deploy Using OpenShift GitOps

We assume that you are in the folder that you have clone/fork the code. For instructions on how to install OpenShift Gitops you can refer to my [OpenShift GitOps Demo](https://github.com/froberge/ocp-gitops-demo) in this [section](https://github.com/froberge/ocp-gitops-demo/blob/main/docs/install-gitops-operator.md)


In this section we will be demontrating how to use `OpenShift` gitops to manage our application and to deploy the application. To to this we need to deploy an other `ArgoCD instance` that will be use for developers to manage the applications

__NOTE__
*   The default `cluster` instance of Argo CD is meant for cluster admin tasks like creating namespace managing role bindings not for day to day application management.

* `The Developer Argo CD instance` will be deploy in it own namespaces and is intented for the developper to use to manage the application.

1. Login to you cluster using the CLI

1. Use kustomize` create the different resources needed to run the demo 
    ```
    oc apply -k setup/overlays/demo
    ```

    This will create all the elements required    
        * __simple-dotnet-gitops__ - The namespace where the argoCD instance for Developer will be install.
        * __simple-dotnet-dev__ - The `DEV` environment for the demo.
        * __simple-dotnet-prod__ - The `PROD` environment for the demo.

