# Kubernetes 

##  Installation of Kubernets on AWS EC2 


## Below are the steps to install the Kubernets on EC2



```sh

Step 1.

setenforce 0

To disable SELinux temporarily

Step 2:

free -h 

The free command gives information about used and unused memory usage and swap memory of a system.

Step 3: 

swapoff -a

To deactivate a swap space, use the command swapoff

Step 4: 

cat <<EOF > /etc/sysctl.d/k8s.conf
net.bridge.bridge-nf-call-ip6tables = 1
net.bridge.bridge-nf-call-iptables = 1
EOF


Step 5: 
Installaton of Docker 

sudo apt-get update

sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
    
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

 sudo apt-get update
 
 sudo apt-get install docker-ce docker-ce-cli containerd.io
 
 Steps 6: 
 
 cat <<EOF > /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg
        https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF

Step 7: 
installation of Kubelet , Kubeadm, Kubectl

Kubelet : The kubelet is the primary "node agent" that runs on each node. 

Kubeadm: Kubeadm is a tool built to provide kubeadm init and kubeadm join as best-practice "fast paths" for creating Kubernetes clusters. 

Kubectl: The Kubernetes command-line tool, kubectl, allows you to run commands against Kubernetes clusters.


yum install kubeadm kubectl kubelet

systemctl status kubelet

kubeadm init

mkdir -p $HOME/.kube
 
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config

sudo chown $(id -u):$(id -g) $HOME/.kube/config


Step 8:

kubectl get pods --all-namespaces

```





