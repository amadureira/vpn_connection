Configure VPN to access other VPN

Please , read this page

https://www.digitalocean.com/community/tutorials/como-configurar-um-servidor-openvpn-no-ubuntu-16-04-pt


# Install

I tested this app on Amazon environment. I've used ami-0b04450959586da29 ami. It is on Sao Paulo Data Center.

Create a ec2 instance. After install the dependences bellow:
```
sudo yum -y install python-pip git
sudo pip install docker-py
sudo pip install ansible>=2.7
git clone https://github.com/quintoandar/hello-devops.git
cd hello-devops/
git apply ~/result.patch
ansible-playbook deploy/tests/test.yml
```

*  Clone repository
*  Apply patch

On hello-devops directory run:
ansible-playbook deploy/tests/test.yml

It will: 
* Install docker and start service
* Create a network and build images
* Deploy containers on machine ( hello-python, hello-node, mysql and rabbitmq )

You could Change some parameters to customazie envirionment. For example  to change queue name.

Those are the  parameters:
* db_name
* db_user
* db_pass
* rabbitmq_queue
* rabbitmq_port 
* rabbitmq_host

For example, To change queue name run:
ansible-playbook deploy/tests/test.yml -e "rabbitmq_queue=test"
Note: You could not change rabbitmq port on build-in container. The rabbitmq default container does not accept it.
