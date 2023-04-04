Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/jammy64"
    
    config.vm.provider "virtualbox" do |vb|
      config.vm.hostname = "airflow-vm"
      vb.memory = "4096"
    end 
    
    config.vm.network "public_network", ip: "192.168.1.200"
    config.vm.synced_folder "./shared", "/opt/airflow"
    config.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "playbook.yml"
    end
end