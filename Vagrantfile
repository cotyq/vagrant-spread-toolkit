$n_nodes = 3
$node_memory = 1024

Vagrant.configure("2") do |config|

  config.vm.provider :virtualbox do |v|
    # Habilita virtualizacion de hardware dentro de la VM
    # v.customize ["modifyvm", :id, "--nested-hw-virt", "on"]
    v.memory = $node_memory
  end

  # Setea la imagen base: Debian 10 de 64 bits
  config.vm.box = "cotyq/vsoa-spread"

  # Se hace un for de 1 a N, donde se configuran N nodos
  (1..$n_nodes).each do |i|
    ## Definición nodo i
    config.vm.define "node-#{i}" do |node|
      # Se setea el hostname
      node.vm.hostname = "vsoa2021-node-#{i}"
      # Configuracion de red
      node.vm.network "private_network", ip: "192.168.1.#{i}"
    end
  end

end

