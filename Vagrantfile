Vagrant.configure("2") do |config|

  config.vm.box = "bento/ubuntu-22.04"

  # Manager Node
  config.vm.define "manager" do |manager|
    manager.vm.hostname = "manager"
    manager.vm.network "private_network", ip: "192.168.56.10"
    manager.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end
  end

  # Worker 1
  config.vm.define "worker1" do |worker|
    worker.vm.hostname = "worker1"
    worker.vm.network "private_network", ip: "192.168.56.11"
    worker.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end
  end

  # Worker 2
  config.vm.define "worker2" do |worker|
    worker.vm.hostname = "worker2"
    worker.vm.network "private_network", ip: "192.168.56.12"
    worker.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end
  end


end
These are the commands we used to allow Jenkins to access Kubernetes (Minikube) during your first pipeline setup.
1. Create Jenkins .kube directory
sudo mkdir -p /var/lib/jenkins/.kube
2. Copy your kubeconfig to Jenkins
sudo cp /home/shree/.kube/config /var/lib/jenkins/.kube/config
3. Give ownership to Jenkins
sudo chown -R jenkins:jenkins /var/lib/jenkins/.kube
4. Create Minikube directory for Jenkins
sudo mkdir -p /var/lib/jenkins/.minikube
5. Copy Minikube certificates
sudo cp -r /home/shree/.minikube/* /var/lib/jenkins/.minikube/
6. Give Jenkins ownership
sudo chown -R jenkins:jenkins /var/lib/jenkins/.minikube
7. Verify Jenkins kubeconfig
sudo -u jenkins kubectl config view
8. Verify Jenkins can access the cluster
sudo -u jenkins kubectl get nodes
When Minikube IP changed
You also ran:
kubectl config view | grep server
sudo -u jenkins kubectl config view | grep server
Then copied the updated config again:
sudo cp /home/shree/.kube/config /var/lib/jenkins/.kube/config
sudo chown jenkins:jenkins /var/lib/jenkins/.kube/config
After that, you edited the Jenkins kubeconfig so the certificate paths pointed to:
/var/lib/jenkins/.minikube/ca.crt
/var/lib/jenkins/.minikube/profiles/minikube/client.crt
/var/lib/jenkins/.minikube/profiles/minikube/client.key
instead of:
/home/shree/.minikube/...
Finally, you verified it with:
sudo -u jenkins kubectl get nodes
