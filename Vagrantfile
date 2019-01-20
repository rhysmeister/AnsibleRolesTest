Vagrant.configure("2") do |config|

  config.vm.define "nginx1" do |nginx1|
    nginx1.vm.box = "centos/7"
    nginx1.vm.hostname = "nginx1"
    nginx1.vm.synced_folder '.', '/vagrant', disabled: true
  end

  config.vm.define "nginx2" do |nginx2|
    nginx2.vm.box = "centos/7"
    nginx2.vm.hostname = "nginx2"
    nginx2.vm.synced_folder '.', '/vagrant', disabled: true
    nginx2.vm.provision 'ansible' do |ansible|
      ansible.groups = {
        "nginx" => ["nginx1","nginx2"],
        "mariadb" => ["mariadb1","mariadb2"],
      }
      ansible.limit = "nginx"
      ansible.playbook = "nginx.yml"
    end
  end

  config.vm.define "mariadb1" do |mariadb1|
    mariadb1.vm.box = "centos/7"
    mariadb1.vm.hostname = "mariadb1"
    mariadb1.vm.synced_folder '.', '/vagrant', disabled: true
  end

  config.vm.define "mariadb2" do |mariadb2|
    mariadb2.vm.box = "centos/7"
    mariadb2.vm.hostname = "mariadb2"
    mariadb2.vm.synced_folder '.', '/vagrant', disabled: true
    mariadb2.vm.provision 'ansible' do |ansible|
      ansible.groups = {
        "nginx" => ["nginx1","nginx2"],
        "mariadb" => ["mariadb1","mariadb2"],
      }
      ansible.limit = "mariadb"
      ansible.ask_vault_pass = true
      ansible.playbook = "mariadb.yml"
    end
  end

end
