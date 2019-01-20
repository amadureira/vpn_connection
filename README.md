Configure VPN to access other VPN

Please , read this page

https://www.digitalocean.com/community/tutorials/como-configurar-um-servidor-openvpn-no-ubuntu-16-04-pt


# Install

I've tested this app on Amazon environment. I've used ami-0b04450959586da29 ami. It is on Sao Paulo Data Center.

Create a ec2 instance. After install run commmands bellow:
```
sudo yum -y install python-pip git
sudo pip install docker-py
sudo pip install 'ansible>=2.7'
git clone https://github.com/quintoandar/hello-devops.git
cd hello-devops/
git apply ~/result.patch
ansible-playbook deploy/tests/test.yml
```

It will install envirionment

You can change some parameters to customazie envirionment. For example  to change queue name.

For example, To change queue name run:
ansible-playbook deploy/tests/test.yml -e "rabbitmq_queue=test"
Note: You could not change rabbitmq port on build-in container. The rabbitmq default container does not accept it.


Those are the parameters:
* db_name - Change db name
* db_user - Change db username
* db_pass - Change db password
* rabbitmq_queue  - Change rabbitmq queue name
* rabbitmq_port   - Change rabbitmq port. Only on external rabbitmq  
* rabbitmq_host   - Change rabbitmq host

You can remove all container with hello_state parammeter.
ansible-playbook deploy/tests/test.yml -e "hello_state=absent"

