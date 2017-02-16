## biemond-orawls-vagrant-puppet

The puppet 4 reference implementation of https://github.com/biemond/biemond-orawls
optimized for linux, Solaris and the use of Hiera

Should work for VMware and Virtualbox

### Details
- CentOS 7.2 Vagrant box
- Puppet 4.8.3
- Vagrant >= 1.8
- Oracle Virtualbox >= 5.1
- VMware fusion >= 8

creates a patched 10.3.6 WebLogic cluster ( admin,node1 , node2 )

Add the all the Oracle binaries to /software

edit Vagrantfile and update the software share
- admin.vm.synced_folder "/Users/edwin/software", "/software"
- node1.vm.synced_folder "/Users/edwin/software", "/software"
- node2.vm.synced_folder "/Users/edwin/software", "/software"

### Software
- jdk-7u79-linux-x64.tar.gz

weblogic 10.3.6
- wls1036_generic.jar
- p17572726_1036_Generic.zip ( 10.3.6.07 BSU Patch)

##Startup the images

###admin server
vagrant up admin

###node1
vagrant up node1

###node2
vagrant up node2


##docker
```bash
vagrant ssh admin
sudo -i
yum install -y epel-release
yum install -y docker-io

wget https://get.docker.com/builds/Linux/x86_64/docker-latest -O docker --no-check-certificate
chmod +x docker
mv docker /usr/bin
```
Add “-s btrfs” in other_args environment variable in docker config file: /etc/sysconfig/docker