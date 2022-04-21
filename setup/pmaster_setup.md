# Installing and Setting up Puppet on CentOS Host

## Setup Puppet Master on Centos Host

```bash
# 1 - Setup Puppet Package Repo
rpm -Uvh https://yum.puppet.com/puppet6-release-el-7.noarch.rpm

# 2 - Install Puppet Server, Vim and Git
yum install -y puppetserver vim git

# 3 - Configure puppetserver sysconfig to use minimm memory
vim /etc/sysconfig/puppetserver

-Xms512M -Xmx512M

# 4 - Start puppetserver service and enable service
systemctl start puppetserver
systemctl status puppetserver
systemctl enable puppetserver
```

## Ensure Puppet Master signs its own certs

Setup puppet agent to connect to puppet server

```bash
# 5 - Command to point puppet master to itself as master:
vim /etc/puppetlabs/puppet/puppet.conf

# Add the following values:
[agent]
server = <puppet_master_fqdn>

# Note: You can identify the fqdn in CentOS7 with this command and argument:
hostname --fqdn
```
