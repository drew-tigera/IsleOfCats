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
You should see a result like this:

`host: Running`
`kubelet: Running`
`apiserver: Running`
`kubectl: Correctly Configured: pointing to minikube-vm at 172.17.17.108`

