Vagrant.configure("2") do |config|
  # 2 vagrant plugins so everything can be connected directly and 
  # update the host file inside each VM provisioned
  config.hostmanager.enabled = true 
  config.hostmanager.manage_host = true
  
### Jenkins  ####
  config.vm.define "jk01" do |jk01|
    jk01.vm.box = "ubuntu/bionic64"
    jk01.vm.hostname = "jk01"
    jk01.vm.network "private_network", ip: "192.168.56.50"
    jk01.vm.provision "ansible" do |ansible|
        ansible.verbose = "v"
        ansible.playbook = "main.yml"  
        ansible.groups = {
            "Jenkins" => ["jk01"]
        }
    end
    jk01.vm.provider "virtualbox" do |vb|
        vb.memory = "4096"
        vb.cpus = 2
    end
  end
  
### Nexus vm  #### 
  config.vm.define "nx01" do |nx01|
    nx01.vm.box = "geerlingguy/centos7"
    nx01.vm.hostname = "nx01"
    nx01.vm.network "private_network", ip: "192.168.56.51"
    nx01.vm.provision "ansible" do |ansible|
        ansible.verbose = "v"
        ansible.playbook = "main.yml"  
        ansible.groups = {
            "Nexus" => ["nx01"]
        }
    end
    nx01.vm.provider "virtualbox" do |vb|
        vb.memory = "2048"
        vb.cpus = 2
    end  
  end
  
### Sonar vm  ####
  config.vm.define "son01" do |son01|
    son01.vm.box = "ubuntu/bionic64"
    son01.vm.hostname = "son01"
    son01.vm.network "private_network", ip: "192.168.56.52"
    son01.vm.provision "ansible" do |ansible|
        ansible.verbose = "v"
        ansible.playbook = "main.yml"  
        ansible.groups = {
            "Sonar" => ["son01"]
        }
    end
    son01.vm.provider "virtualbox" do |vb|
        vb.memory = "4096"
        vb.cpus = 2
    end
  end  
end