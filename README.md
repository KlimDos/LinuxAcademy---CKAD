# 1. Setup playground
 - create 3 instances
 - manually ssh into each and set new pass (same for all 3)
 - fill in ansible inventory
 - test `ansible -m ping -i playground/inventory.yaml all`
 - provision all 3 nodes `ansible-playbook -i playground/inventory.yaml playground/playbook.yaml`

 - ssh to master
 - initiate cluster `sudo kubeadm init --pod-network-cidr=10.244.0.0/16`
 - add cluster info from `/etc/kubernetes/admin.yaml` into your local kubectl config (replace IP by dns name)
 
 - ssh into each node
 - join cluster via command kubeadm init you ran during the setup in master

 - install flannel CNI `kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/bc79dd1505b0c8681ece4de4c0d86c5cd2643275/Documentation/kube-flannel.yml`