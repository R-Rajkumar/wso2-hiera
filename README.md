# wso2-hiera
wso2 hiera for common deployment patterns

# How to use the developer environment
Follow below steps to setup the development environment for implementing new Puppet modules:

- Install VirtualBox
- Install Vagrant
- Clone wso2-hiera-vagrant-setup - https://github.com/R-Rajkumar/wso2-hiera.git

### wso2-hiera-vagrant-setup

- config.yaml.sample contains all the required information for the Dev environment.

 - servers section list down the puppet module that needs to be tested.
 - you can add more servers with the same structure
 - make it to false in **enabled** section if you do not want to spin a VM for that particular server.

- Provide the file paths for the following based on your environment.

 - hiera_path : hiera data files location
 - manifests_path : manifest files location
 - module_path : puppet modules location
 - hiera_config_path : hiera.yaml config file location
 - working_directory : relative path in the guest machine

- Rename config.yaml.sample to config.yaml.

- You can use the following commands to spin VMs.

 - vagrant up : Will spin all the servers mentioned in the config.yaml (enabled flag should be true or not present)
 - vagrant up hostname : Will spin a server which has the mentioned hostname (eg : vagrant up dev-sandbox-apim.local.dev.wso2.org)

### Note

1. If you are running wso2am puppet module, wso2am-1.9.1.zip product zip file should be placed under files directory in wso2am puppet module.
2. Jdk tar file should be placed under files directory in wso2base puppet module.
3. If you don't have any files in the /etc/puppet/files directory, you can comment following line in Vagrant file.
server_config.vm.synced_folder("/etc/puppet/files", "/puppet-files")

