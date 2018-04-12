# ansible-redcap-aws
Ansible script to deploy a redcap instance on CentOS in AWS

*To Install ansible:*
http://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html

*For use with ansible vault:*
http://docs.ansible.com/ansible/devel/user_guide/vault.html

Warning: The /etc/resolve role assumes a us-west-2 ip range default from terraform-redcap-aws

See: https://github.com/razorlabs/terraform-redcap-aws

*Usage:*

1) Download the preferred version of redcap from:
https://community.projectredcap.org/index.html#

2) Place the redcap zip file in /redcap_vars/files/

3) Edit the vars in redcap_vars/vars/provision_redcap.yml

  remote_user: typically ec2-user

  organization: Your organization name

  whitelist_ips: IP address for web access

  redcap_zipfile: (ex: ../files/redcap8.1.5.zip)

  mysql_user: the root mysql user name

  mysql_password: the root mysql password

  redcap_db_username: the redcap mysql db user

  redcap_db_userpassword: the redcap mysql db user password

  rds_mysql_host: the rds host address

  salt: (for use with ansible-vault)

4) With your aws key added to your ssh key-chain run:
ansible-playbook -i ./hosts ./install_redcap.yml --user=[remote-aws-user-with-sudo-priv]

5) Go to http://<elastic_ip_address>/redcap/install.php to complete the installation

