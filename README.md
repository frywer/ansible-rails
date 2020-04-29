Tested with Ubuntu 18.04

### 1. Ansible installation

```ruby
sudo apt-add-repository -y ppa:ansible/ansible
sudo apt-get update
sudo apt-get install -y ansible
ansible-galaxy install rvm.ruby
ansible-galaxy install crushlovely.imagemagick
```
### 2. Clone repository
remove default ansible configuration

```ruby
sudo rm -rf /etc/ansible
cd
git clone git@git.gladsquid.com:gladsquid/ansible.git
sudo mv ./ansible /etc

```

### 3. Set-Up new server
```ruby
ssh-copy-id root@1.2.3.4
```

### 4. Update variables

deployment user and password
in ansible-rails/roles/user/vars/
```ruby
worker_password: password
common_public_key: ssh-rsa xxx
```
mysql root password
in ansible-rails/roles/mysql/tasks/main.yml
```ruby
mysql_user
```
### 5. Ping servers

```ruby
cd /etc/ansible
ansible -i ./hosts deploy -m ping
```


### 6. Run ansible

```ruby
ansible-playbook -i ./hosts ./servers.yml
```

