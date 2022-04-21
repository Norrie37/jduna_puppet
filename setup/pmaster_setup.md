# Setup Puppet Master on Centos Host

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
