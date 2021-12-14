Vagrant.configure("2") do |config|
    # Master
    config.vm.define:"master" do |cfg|
        cfg.vm.box = "centos/7"
        cfg.vm.provider:vmware_desktop do |vw|
            vw.gui = true   # Launch guest with a GUI. This defaults to false
            vw.vmx['displayname'] = "master"
            vw.vmx["numvcpus"] = "8"
            vw.vmx["memsize"] = "16384"
        end
        cfg.vm.host_name="master"
        #cfg.vm.synced_folder ".", "/vagrant", type: "nfs"
        cfg.vm.network "private_network", ip: "192.168.139.10"
        cfg.vm.network "forwarded_port", guest: 22, host: 19214, auto_correct: false, id: "ssh"
    end

    # Worker1
    config.vm.define:"worker-1" do |cfg|
        cfg.vm.box = "centos/7"
        cfg.vm.provider:vmware_desktop do |vw|
            vw.gui = true
            vw.vmx['displayname'] = "worker-1"
            vw.vmx["numvcpus"] = "4"
            vw.vmx["memsize"] = "4096"
        end
        cfg.vm.host_name="worker1"
        #cfg.vm.synced_folder ".", "/vagrant", type: "nfs"
        cfg.vm.network "private_network", ip: "192.168.139.11"
        cfg.vm.network "forwarded_port", guest: 22, host: 19211, auto_correct: false, id: "ssh"
        cfg.vm.provision "shell", path: "bash_ssh_conf_4_CentOS.sh"
    end

    # Worker2
#     config.vm.define:"worker-2" do |cfg|
#         cfg.vm.box = "centos/7"
#         cfg.vm.provider:vmware_desktop do |vw|
#             vw.name="worker -2"
#             vw.customize ["modifyvm", :id, "--cpus", 4]
#             vw.customize ["modifyvm", :id, "--memory", 4096]
#         end
#         cfg.vm.host_name="worker2"
#         #cfg.vm.synced_folder ".", "/vagrant", type: "nfs"
#         cfg.vm.network "private_network", ip: "192.168.139.12"
#         cfg.vm.network "forwarded_port", guest: 22, host: 19212, auto_correct: false, id: "ssh"
#         cfg.vm.provision "shell", path: "bash_ssh_conf_4_CentOS.sh"
#     end
end