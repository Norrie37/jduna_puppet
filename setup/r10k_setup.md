# Setting up r10k on CentOS Host

## 1 - Install r10k

R10k is a tool used to deploy code from your git-repo to the puppet master server.

```bash
# Use Ruby that was installed with Puppet Server
vim .bash_profile

# Add the following line before the PATH:
PATH=$PATH:/opt/puppetlabs/puppet/bin

# Start a new bash session to ensure access to this new path for ruby:
exec bash

# Make changes take effect:
source .bash_profile

# Run the gem command to ensure ruby gems is working:
gem

# Install r10k:
gem install r10k
```

## 2 - Setting up r10k to point to my remote repo

Create home directory for r10k in puppet master:

```bash
mkdir /etc/puppetlabs/r10k

# Setup r10k.yaml config file
vim /etc/puppetlabs/r10k/r10k.yaml
```

```yaml
# Fill in the following contents:
---
:cachedir: '/var/cache/r10k'

:sources:
        :my-org:
                remote: 'https://github.com/Norrie37/td_puppet.git'
                basedir: '/etc/puppetlabs/code/environments'
```

## 3 - Test Puppet by doing an agent run

Do initial puppet run on node

```bash
# Puppet run command:
puppet agent -t
```