Vagrant.configure("2") do |config|
    servers=[
        {
          :hostname => "control",
          :box => "bento/ubuntu-18.04",
          :ip => "192.168.56.15",
          :ssh_port => '2200'
        },
        {
          :hostname => "node1",
          :box => "bento/ubuntu-18.04",
          :ip => "192.168.56.25",
          :ssh_port => '2201'
        },
        {
          :hostname => "node2",
          :box => "bento/ubuntu-18.04",
          :ip => "192.168.56.24",
          :ssh_port => '2202'
        },
		{
          :hostname => "node3",
          :box => "bento/ubuntu-18.04",
          :ip => "192.168.56.22",
          :ssh_port => '2203'
        }
      ]

    servers.each do |machine|
        config.vm.define machine[:hostname] do |node|
            node.vm.box = machine[:box]
            node.vm.hostname = machine[:hostname]
            node.vm.network :private_network, ip: machine[:ip]
            node.vm.network "forwarded_port", guest: 22, host: machine[:ssh_port], id: "ssh"
            node.vm.provider :virtualbox do |vb|
                vb.customize ["modifyvm", :id, "--memory", 1024]
                vb.customize ["modifyvm", :id, "--cpus", 2]
				
            end
        end
    end
end


