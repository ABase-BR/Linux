## 04 - Introdução ao Vagrant

## 04.1 - O que temos para trabalhar ?
Podemos ter disponível uma maquina normal com 4 GB e um Dual Core rodando , mais e quando não temos e precisamos virtualizar alguma maquina ou algum projeto ? Vou mostrar que é possível criar um servidor com apenas 256 MB e ainda adicionar ele na deep web ou podemos criar uma maquina virtual com ambiente gráfico XFCE com poucos recursos. Não temos desculpa para falar que na minha maquina funcionava.


## 04.2 - O que é o Vagrant?
Basicamente ele vai ser responsável por gerenciar nossas maquinas virtuais. Podemos usar o Virtualbox , VMware , AWS e entre outros serviços.

Nas nossas aulas vamos usar a versão Minimal do Debian , podemos encontrar ele no seguinte link

https://atlas.hashicorp.com/minimal

Nesse link temos diversos sistemas que você pode usar como bem entender , mais em nossas aulas vamos usar

https://atlas.hashicorp.com/minimal/boxes/jessie64


## 04.3 - Podemos configurar automaticamente
Para configurar automaticamente a instalação de softwares podemos usar o scripts em shell , chef e até o Puppet.

Vamos usar scripts para automatizar a criação de servidores (LAMP) e até um servidor (DeepWeb) com conteúdo estático.

## 04.4 - Arquivo Vagrantfile
Basicamente o arquivo Vagrantfile será responsável pela configuração de nossa maquina virtual , podemos ver um arquivo padrão de exemplo.

Podemos iniciar um arquivo da seguinte forma , vamos iniciar usando o ** vagrant init ** seguido da nossa maquina virtual ** debian/jessie64 ** .

```sh
vagrant init debian/jessie64
```

Vai ser gerado um arquivo ** Vagrantfile ** padrão , podemos ver ele em

```sh

# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "debian/jessie64"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  # config.ssh.forward_agent = true

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Don't boot with headless mode
  #   vb.gui = true
  #
  #   # Use VBoxManage to customize the VM. For example to change memory:
  #   vb.customize ["modifyvm", :id, "--memory", "1024"]
  # end
  #
  # View the documentation for the provider you're using for more
  # information on available options.

  # Enable provisioning with CFEngine. CFEngine Community packages are
  # automatically installed. For example, configure the host as a
  # policy server and optionally a policy file to run:
  #
  # config.vm.provision "cfengine" do |cf|
  #   cf.am_policy_hub = true
  #   # cf.run_file = "motd.cf"
  # end
  #
  # You can also configure and bootstrap a client to an existing
  # policy server:
  #
  # config.vm.provision "cfengine" do |cf|
  #   cf.policy_server_address = "10.0.2.15"
  # end

  # Enable provisioning with Puppet stand alone.  Puppet manifests
  # are contained in a directory path relative to this Vagrantfile.
  # You will need to create the manifests directory and a manifest in
  # the file default.pp in the manifests_path directory.
  #
  # config.vm.provision "puppet" do |puppet|
  #   puppet.manifests_path = "manifests"
  #   puppet.manifest_file  = "default.pp"
  # end

  # Enable provisioning with chef solo, specifying a cookbooks path, roles
  # path, and data_bags path (all relative to this Vagrantfile), and adding
  # some recipes and/or roles.
  #
  # config.vm.provision "chef_solo" do |chef|
  #   chef.cookbooks_path = "../my-recipes/cookbooks"
  #   chef.roles_path = "../my-recipes/roles"
  #   chef.data_bags_path = "../my-recipes/data_bags"
  #   chef.add_recipe "mysql"
  #   chef.add_role "web"
  #
  #   # You may also specify custom JSON attributes:
  #   chef.json = { mysql_password: "foo" }
  # end

  # Enable provisioning with chef server, specifying the chef server URL,
  # and the path to the validation key (relative to this Vagrantfile).
  #
  # The Opscode Platform uses HTTPS. Substitute your organization for
  # ORGNAME in the URL and validation key.
  #
  # If you have your own Chef Server, use the appropriate URL, which may be
  # HTTP instead of HTTPS depending on your configuration. Also change the
  # validation key to validation.pem.
  #
  # config.vm.provision "chef_client" do |chef|
  #   chef.chef_server_url = "https://api.opscode.com/organizations/ORGNAME"
  #   chef.validation_key_path = "ORGNAME-validator.pem"
  # end
  #
  # If you're using the Opscode platform, your validator client is
  # ORGNAME-validator, replacing ORGNAME with your organization name.
  #
  # If you have your own Chef Server, the default validation client name is
  # chef-validator, unless you changed the configuration.
  #
  #   chef.validation_client_name = "ORGNAME-validator"
end

```

Esse é o arquivo padrão , vamos criar o nosso.

Mais como aprendemos anteriormente vamos usar o **Vagrantfile**.

```sh
# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  #Nome da nossa VM
  config.vm.define "testvm" do |testvm|
    #VM Vagrant que vamos usar
    testvm.vm.box = "minimal/jessie64"
    # IP que vamos usar
    testvm.vm.network :private_network, ip: "192.168.33.21"
    #Nome do script para automatizar instalação
#   testvm.vm.provision "shell", path: "webserver.sh"
  end

  #Qual provider que vamos utilizar
  config.vm.provider "virtualbox" do |v|
    #Memoria que vamos utilizar
    v.customize ["modifyvm", :id, "--memory", "1024"]
  end

end

```

Tudo que precisamos é criar um **Vagrantfile** , podemos usar até o **nano** para isso.

Após criado vamos subir nossa maquina usando

```sh
vagrant up
```

## 04.5 - Iniciando uma maquina
Para iniciar uma maquina virtual podemos usar o comando ** vagrant up ** no diretório que estiver o arquivo ** Vagrantfile ** .


Para iniciar é

```sh
vagrant up
```

Podemos ver que nossa maquina vai ser iniciada , como ela só vai iniciar (pois não tem nenhum arquivo sendo executado na sua inicialização) vai ser preciso só baixar a maquina virtual (claro se não estiver em sua maquina) , caso ela esteja ela só vai iniciar.

Assim poupamos muito tempo , tempo para criar uma nova maquina , tempo para restaurar um estado de maquina e tempo para ter acesso aquelas versões que não usamos mais.

## 04.6 - Acessando maquina virtual
```sh
vagrant ssh
```

## 04.7 - Pausar estado da maquina
```sh
vagrant halt
```

## 04.8 - Instalar scripts na maquina

## 04.9 - Destruir maquinas
```sh
vagrant destroy
```

## 04.10 - Criar mais uma maquina ao mesmo tempo


## 04.11 - Criando maquina virtual Minimal Debian


## 04.12 - Criando maquina virtual Debian Jessie XFCE

## 04.13 - Criando maquina virtual Kali Linux usando pentest-env

Baixando a maquina virtual

Podemos usar uma maquina virtual chamada ** pentest-env ** que é uma ** VM Kali ** , nos exemplos eu vou usar uma ** Debian Jessie ** que é semelhante.

```sh
git clone https://github.com/Sliim/pentest-env
```

Assim que baixar a maquina , vamos entrar no diretório ** pentest-env ** .

```sh
cd pentest-env
```

Para subir a nossa maquina vamos usar
```sh
vagrant up
```

Só precisamos aguardar que nossa maquina virtual Kali será iniciada. OBS: Ela vem configurada com outras maquinas virtuais (como laboratórios para estudo DVWA entre outras ) que podem ser iniciadas , mais precisamos de mais processamento já que esse projeto vem configurado com 2 GB pra VM Kali.
