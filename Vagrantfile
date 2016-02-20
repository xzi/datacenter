servers = ['vm1','vm2','vm3','vm4','vm5','vm6','vm7','vm8']

Vagrant.configure("2") do |config|
  config.vm.box     = 'vsphere'
  config.vm.box_url = './dummy.box'

  servers.each do |hostname|
    config.vm.define "#{hostname}" do |build|
      build.vm.hostname = "#{hostname}.xzicloud.com"
      config.vm.provision "shell" do |shell|
        shell.inline = "echo Vagrant name defined as: #{hostname}"
      end
      build.vm.provider :vsphere do |vsphere|
        vsphere.host                  	= 'vc1.xzicloud.com'
        vsphere.name                  	= "#{hostname}.xzicloud.com"
        vsphere.data_center_name	  	  = '55Illinois'
        vsphere.compute_resource_name 	= 'DCS-Cloud'
        vsphere.resource_pool_name    	= 'vagrant-pool'
        vsphere.template_name         	= 'Templates/vagrant/photon_tp2_base'
        vsphere.vm_base_path          	= 'Compute/vagrant-machines'
        vsphere.data_store_name		= 'vsanDatastore'
        vsphere.user     = 'vagrant@vsphere.local'
        vsphere.password = 'vagrant'
        vsphere.insecure = true
        config.vm.provision "shell" do |shell|
          shell.inline = "echo vSphere name defined as: #{hostname}.xzicloud.com"
        end
      end
    end
  end
end
