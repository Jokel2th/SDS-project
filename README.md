# SNS-Project

## Setting up Kubernetes cluster

### Using Stacked control plane and etcd nodes

join control plane and worker nodes to the cluster

`kubeadm join 192.168.0.200:6443 --token 9vr73a.a8uxyaju799qwdjv --discovery-token-ca-cert-hash sha256:7c2e69131a36ae2a042a339b33381c6d0d43887e2de83720eff5359e26aec866 --control-plane --certificate-key f8902e114ef118304e561c3ecd4d0b543adc226b7a07f675f56564185ffe0c07`

Apply the CNI plugin of your choice: Follow these instructions to install the CNI provider. Make sure the configuration corresponds to the Pod CIDR specified in the kubeadm configuration file if applicable.

`kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"`

## Deployment

### Using Pre-Built Container Images

This option offers you pre-built public container images that are easy to deploy
by deploying the [release manifest](./release) directly to an existing cluster.

**Prerequisite**: a running Kubernetes cluster (either local or on cloud).

1. Clone this repository, and go to the repository directory
1. Run `kubectl apply -f ./release/kubernetes-manifests.yaml` to deploy the app.
1. Run `kubectl get pods` to see pods are in a Ready state.
1. Find the IP address of your application, then visit the application on your
   browser to confirm installation.

   ```sh
   kubectl get service/frontend-external
   ```
