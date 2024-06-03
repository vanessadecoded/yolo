Vagrant.configure("2") do |config|
    config.vm.box = "geerlingguy/ubuntu2004"
    config.vm.network "forwarded_port", guest: 3000, host: 4000  
    config.vm.network "forwarded_port", guest: 5000, host: 6000  
  
    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "yolo_playbook.yaml"
      ansible.verbose = "vv" 
    end
  end