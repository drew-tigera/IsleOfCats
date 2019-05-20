# IsleOfCats
Documents and labs for the Isle of Cats lecture

Please download a copy of the slides and then use this for the labs.

In order to do these labs you will need a copy of Minikube running on your laptop.

Please see here for instructions on installing Minikube:

https://kubernetes.io/docs/tasks/tools/install-minikube/

## Hands on Lab

1. Open up a command prompt on your system that has Minikube already installed.
2. Run the following command to setup Minikube so that it can run Calico:

`minikube start --host-only-cidr 172.17.17.1/24 --network-plugin=cni --enable-default-cni --extra-config=kubelet.network-plugin=cni --extra-config=kubelet.pod-cidr=192.168.0.0/16 --extra-config=controller-manager.cluster-cidr=192.168.0.0/16 --extra-config=controller-manager.allocate-node-cidrs=true`

*Please note we currently have an issue open with Minikube to make this a bit easier!*

3. Once Minikube is up and running - it could take a few minutes depending on how fast your network is - run the following command:
`minikube status`

Minikube should be listed as running, also make of note of the IP address assigned to your Minikube system. You will need that for futher labs.

4. Now that Minikube is ready we can install Calico on top:

`kubectl apply -f https://docs.projectcalico.org/v3.6/getting-started/kubernetes/installation/hosted/kubernetes-datastore/calico-networking/1.7/calico.yaml`

That will install the latest version of Calico. Give it a few minutes to install and settle. 

`kubectl get nodes --all-namespaces` to verify all the nodes are ready.

5. Once all the Calico nodes are running we are ready to do the following tutorial:
https://docs.projectcalico.org/v3.7/security/stars-policy/

