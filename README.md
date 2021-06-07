# ADL_LRS_K8S

Built upon [adl-lrs-docker](https://github.com/vbhayden/adl-lrs-docker) to implement [adlnet's ADL_LRS](https://github.com/adlnet/ADL_LRS) with a touch of Kubernetes.


## Setup Kubernetes cluster

Setup a Kubernetes or a K3S cluster in the cloud or on premise.

## HTTPS Setup
This application is fully functional only over HTTPS. So head over to [noip.com](noip.com) to obtain a temporary hostname for free. 

In the files `ssl_certs.yml` and `nginx-ingress.yml`, replace `<domain>` with your temporary domain. Also replace `<email>` in the `ssl_certs.yml` file.

Then execute 

` kubectl create ns cert-manager`
  
` kubectl apply -f https://github.com/jetstack/cert-manager/releases/download/v0.13.0/cert-manager.yaml`
 
 
This will install [Cert-Manager](https://cert-manager.io/) in a separate namespace. For more information on how configure Cert-Manager, click [here](https://medium.com/flant-com/cert-manager-lets-encrypt-ssl-certs-for-kubernetes-7642e463bbce)

## Deployment

After setting up a kubernetes cluster and HTTPS support

From the project directory run:

`kubectl create -f ./k8s/`



