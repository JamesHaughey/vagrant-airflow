IMAGE_NAME = "debian/buster64"

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false

  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 2
  end

  config.vm.define "airflow-controller" do |master|
    master.vm.box = IMAGE_NAME
    master.vm.network "private_network", ip: "192.168.50.20"
    master.vm.hostname = "airflow-controller"

    master.vm.provision "ansible_hadoop", type:"ansible" do |ansible|
      ansible.playbook = "playbooks/install_airflow.yml"
      # ansible.raw_arguments = [
      #   "-e 'ansible_python_interpreter=/usr/bin/python3'"
      # ]
      # ansible.extra_vars = {
      #   "controller_ip" => "192.168.50.10",
      #   "node1_ip" => "192.168.50.11",
      #   "node2_ip" => "192.168.50.12",
      # }
    end
  end

end