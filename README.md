# ansible-redis-replication
Simple redis replication using ansible as configuration manager

### Run Ansible playbook from local
create a ssh config file to directly apply / provision the changes through bastion (ssh)
```
Host <ip-pattern>
  User <ssh-user>
  ProxyCommand ssh -W %h:%p %r@<bastion-ip>
  ForwardAgent yes
  StrictHostKeyChecking no
  UserKnownHostsFile /dev/null
```

### Install Ansible
we are going to use virtualenv approach for better isolation and your system cleanliness.
```
# create python virtualenv
python3 -m venv ~/ansienv

#activate virtualenv
source ~/ansienv/bin/activate

#optional, upgrade your pip (make sure at least you have pip-21.x
pip install --upgrade pip

#install the requirement
cd /path/to/devops-central/ansible/
pip install -Ur requirements.txt

#test your ansible
ansible -m ping localhost

#it should return
localhost | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```

### How to run ansible playbook
`ansible-playbook -i inventory/<inventory path>/ playbooks/<playbook file>.yaml`