# ADL_LRS_K8S

Built upon [adl-lrs-docker](https://github.com/vbhayden/adl-lrs-docker) to implement [adlnet's ADL_LRS](https://github.com/adlnet/ADL_LRS) with a touch of Kubernetes.


## To deploy on Kubernetes cluster locally
Install [minikube](https://minikube.sigs.k8s.io/docs/start/) and start the cluster using 

`minikube start --vm=true`

Next, from the project directory run:

`kubectl create -f ./k8s/`

After that, execute:

`minikube ip`

And paste the output into a web browser.

## HTTPS Setup
This application is fully functional only over HTTPS. So head over to [noip.com](noip.com) to obtain a temporary hostname for free. 
Point the hostname to the IP address obtained from minikube ip in the previous step. 

Then execute 

` kubectl create ns cert-manager`
  
` kubectl apply -f https://github.com/jetstack/cert-manager/releases/download/v0.13.0/cert-manager.yaml`
 
 
This will install [Cert-Manager](https://cert-manager.io/) in a separate namespace. For more information on how configure Cert-Manager, click [here](https://medium.com/flant-com/cert-manager-lets-encrypt-ssl-certs-for-kubernetes-7642e463bbce)

Once configured, find the certificated.yml file inside the k8s directory and modify the **commonName** and the **dnsNames** to the domain from noip.com. Then run: 

`kubectl apply -f ./k8s/certificates.yml`

