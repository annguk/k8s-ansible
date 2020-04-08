# k8s-ansible
kubernetes cluster preinstall ansible playbook

Ansible

$ ssh-keygen

- all yes

-- client deploy
$ ssh-copy-id root@192.168.137.201

$ yum install -y epel-release

$ yum install -y ansible

Use
$ ansible-playbook -i inventory preinstall.yaml

$ reboot

Only Master

$ kubeadm init --pod-network-cidr=172.16.0.0/16 --apiserver-advertise-address=192.168.137.201

$ mkdir -p $HOME/.kube
$ cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
$ chown $(id -u):$(id -g) $HOME/.kube/config

Installing a pod network add-on

$ kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml 

Node check
$ kubectl get pod -n kube-system 

Node join
$ kubeadm join 192.168.137.201:6443 --token data --discovery-token-ca-cert-hash sha256:data
 
