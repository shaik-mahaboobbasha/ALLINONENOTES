# ALLINONENOTES

Git
Maven
Sonarqube
Jenkins
Docker
chef 
Ansible
Kubernetes

ssh -i key.pem root @ipaddress
echo -n "basha" | base64
echo "basha" | openssl base64 -d; echo

Git:

git remote -v
git remote add yrl
git init
git config --global user.name= King
git config --global user.password= king123
git config --global alias.l = log
git config --global --unset alias.l

touch file{1..20}
git status
git add .
git commit -m "label message"
git status 
git log
git log --oneline
git show commitId
git checkout
git branch
git branch --list
git branch <branchname>
git checkout -b <branchname>
git checkout <branchname>
git merge
git rebase
git cherry-pick commitId
git merge --abort
git stash --list
git stash save <stashname>
git stash show -p <StashId>
git stash pop
git stash apply
git stash drop <stashId>
git push --tags
git tag V1.1 commitId
git tag -d <tagname>
git branch -d <branchname>
git push origin <branchname>
git push origin -d <tagname>
git push origin -d <branchname>
git clone
git pull
git fetch 
git merge
git pull =git fetch+ git merge



Maven:

mvn archetype:generate
mvn validate
mvn compile
mvn test-compile
mvn test
mvn package
mvn integration-test
mvn verify
mvn install
mvn deploy

mvn install sonar:sonar

Docker:

docker search <imagename>
docker pull <imagename>
docker run -it -P 8080:81 <imagename>
docker run -itd -P 8080:81 <imagename>
docker run -it -P 8080:81 --name <containername> <imagename>
docker run -itd -P 8080:81 --name <containername> <imagename>
docker exec -it -P 8080:81 --name <containername> <imagename> 
docker ps 
docker ps -A
docker ps -qA
docker attach <containerId>
Exit
Vi dockerFile
docker built -t <Imagename> PathOfTheDockerFile
docker commit <ConatinerId> <Imagename>
docker conatiner export <conatinername> > myImage.tar
docker image import myImage.tar <imagename>
docker inspect <conatinerId>
docker inspect <imagename>
docker history <imagename>
docker inspect <volumename>
docker inspect <networkname>
docker stop <conatinerId>
docker start <containerId>
docker pause <containerId>
docker rm <containerId>
docker conatiner prune [Delete unused conatiner in oneshot]
docker rmi <Imagename>
docker volume --list
docker create volume <volumename>
docker run -itd --name <containername> -v <volumename>:/tmp <Imagename>
docker rm <volumename>
docker network --list
docker create network --subnet= 172.16.0.0/16 -d bridge <Networkname>
docker create network --subnet= 172.16.0.0/16 -d host <Networkname>
docker create network --subnet= 172.16.0.0/16 -d none <Networkname>
docker run -itd --name <containername> --network=<networkname> -v <volumename>:/tmp <Imagename>
docker rm <networkname>
docker network connect <networkname> <conatinerId>
docker network disconnect <networkname> <containerId>


Chef:

chef generate cookbookname <cookbookname>
cd <cookbookname>
chef generate recipe <recipename>
vi cookbookname/recipes/recipes.rb
package tree do
action: create 
content 'Installing the tree package in the Linux!!'
end
chef spec ruby -c cookbookname/recipes/recipes.rb
chef-client -zr recipe[cookbookname::recipename]


knife generate cookbookname <cookbookname>
cd <cookbookname>
knife generate recipe <recipename>
vi cookbookname/recipes/recipes.rb
package tree do
action: create 
content 'Installing the tree package in the Linux!!'
end
knife spec ruby -c cookbookname/recipes/recipes.rb
knife upload cookbook <cookbookname>
knife node run_list add/set recipe[cookbookname::recipename]
chef-client 
mkdir roles
cd roles
vi roles.rb
name <rolename>
description 'adding the role'
run_list recipe[cookbookname::recipename]
knife role from files roles/roles.rb
knife node run_list add/set roles[devops]
knife bootstrap 172.16.0.0 --ssh-user root --sudo -i key.pem -N <nodename>

Ansible:

vi /etc/ssh/sshd_config
password authentication Yes
ssh root@Ipaddress
ssh key-gen
ssh copy-id <Ipaddress>

1.Ad-hoc 
2.Modules
3.Playbook

Ad-hoc:
ansible <groupname> -a "mkdir Foldercreation"

Modules:
ansible <groupname> -b -m yum -a "pkg=httpd state=present"

Playbook:

hosts: <groupname>
user: root
connection: ssh
become: Yes
gathering_facts: yes

tasks:
action: yum  name=httpd state=present
command: yum install httpd

Ansible-playbook <filename>

ansible-vault create <filename>
ansible-vault edit <filename>
ansible-vault view <filename>
ansible-vault encrypt <filename>
ansible-valut decrypt <filename>

ansible-galaxy init <Rolename>
