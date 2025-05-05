# How to deploy your first app on local kubernetes cluster using minikube
  This guide will tell you how to create a local kubernetes cluster and ssh into it

## Install kubectl
   1. Visit https://kubernetes.io/docs/tasks/tools/ and select the OS where you need to install kubectl
   2. Install kubectl using curl and run the right curl command based on your local machine architecture
      ```
      For x86-64 -  curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
   3. Execute the final install command
      ```
      sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
   4. Test the version
      ```
      kubectl version --client
 ## Install minikube 
  1. Search Install minikube on google
  2. Select the requirements to run the curl command
  3. Execute the commands
     ```
     curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
     sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
  4. Start your cluster
     ```
     minikube start --memory=4096 --driver=docker
  Note : The driver can be docker , virtual box or anything. You need to install it before running the command
  ## Deploy a Pod
  1. ```
     kubectl get nodes
  2. Create pod.yml file 
     ```
     vi pod.yml     
   Note : You can get sample pod.yml file from the internet
   
  3. Run the command to create your first kubernetes pod
     ```
     kubectl create -f pod.yml
  4. Check your detailed description of pod
     ```
     kubectl get pods -o wide
  5. To ssh into your minikube cluster
     ```
     minikube ssh
     curl [ip_address_of_pod]
