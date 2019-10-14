To run this provisioner from an Azure Cloud Shell environment, these are the commands you will need to issue

```
virtualenv -p /usr/bin/python2.7 skylight-env
source skylight-env/bin/activate
pip install requests-credssp
pip install pywinrm[credssp]
pip install ansible
pip install packaging
pip install msrestazure
pip install ansible[azure]
pip install cryptography==2.4.2

git clone https://github.com/mgmt-sa-tiger-team/skylight.git
cd skylight/vars/
cp vars/main.yml vars/custom.yml

# ADD YOUR AZURE SETTINGS
vi vars/custom.yml

# ADD YOUR TOWER LICENSE
#vi tower_license.json
{
    "company_name": "1987", 
    "contact_email": "seval124@gmail.com", 
    "contact_name": "chris Job", 
    "hostname": "e2e0b6a241f444e1b474306aacae4e91", 
    "instance_count": 10, 
    "license_date": 1569441776, 
    "license_key": "5badb59683557b51b9791c0ffd3ea0ea7d99bc9220405e81b3b35de6c0fc428a", 
    "license_type": "enterprise", 
    "subscription_name": "Red Hat Ansible Tower, Standard (10 Managed Nodes) Trial", 
    "trial": true
}

# RUN THE PROVISIONER
ansible-playbook provision.yml -c paramiko
```

