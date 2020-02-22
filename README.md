## links for the Introduction to DevOps Tools hands-on training course.

### Chapters 1, 2 & 3

https://www.virtualbox.org/wiki/Downloads 

https://www.vagrantup.com/downloads.html

https://aws.amazon.com/

### Chapter 4

https://packer.io/intro/
https://github.com/dmccuk/packer_demo

### Chapter 5

https://www.terraform.io/intro/index.html
https://github.com/dmccuk/terraform_first.git
https://aws.amazon.com/ec2/instance-types/
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html
https://cloud-images.ubuntu.com/locator/ec2/ 

### Chapter 6

https://github.com/dmccuk/terraform_modules.git

If you see this message in the terraform output:

````
(remote-exec): E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavailable)
````

It’s caused by an unattended update when the server comes online. I’ve seen this process in-use which I think needs to complete before we can attempt to run our install:

````
/bin/sh /usr/lib/apt/apt.systemd.daily lock_is_held install
````

To resolve the issue in the short term, simply add “sleep 120” to the top of the build script in the files directory.

````
vagrant@devops-box:~/terraform_modules/stack$ ls -al files/
total 24
drwxrwxr-x 2 vagrant vagrant 4096 Feb 21 17:31 .
drwxrwxr-x 4 vagrant vagrant 4096 Feb 21 17:36 ..
-rw-rw-r-- 1 vagrant vagrant  721 Feb 21 17:30 gitlab_install.sh
-rw-rw-r-- 1 vagrant vagrant  573 Feb 21 17:14 jenkins_install.sh
-rw-rw-r-- 1 vagrant vagrant  252 Feb 21 17:14 scripts.sh
-rw-rw-r-- 1 vagrant vagrant  211 Feb 21 17:14 standard.sh

vagrant@devops-box:~/terraform_modules/stack$ cat files/standard.sh
#!/bin/bash
sleep 120  add this line.
sudo apt update -yq
sudo DEBIAN_FRONTEND=noninteractive apt upgrade -yq
sudo apt install wget curl git python3-minimal -yq
#fix for python3 symlink
#ln -s /usr/bin/python3.5 /usr/bin/python
vagrant@devops-box:~/terraform_modules/stack$
````

### Chapter 7 & 9

https://github.com/dmccuk/ansible_nginx
https://www.meetup.com/Ansible-London/
https://gist.github.com/rtapadar/2824729b7bad87dd7173f6bbbe5101b8
https://docs.ansible.com/ansible/latest/reference_appendices/config.html#ansible-configuration-settings 

For example, this ansible page on installing packages on ubuntu, gives you practical examples and explanations of all the options available: https://docs.ansible.com/ansible/latest/modules/apt_module.html


Other useful ansible pages for this exercise are:
•	https://docs.ansible.com/ansible/latest/modules/service_module.html (Ansible Services)
•	https://docs.ansible.com/ansible/latest/modules/template_module.html (Ansible templates)
•	https://docs.ansible.com/ansible/latest/user_guide/playbooks_intro.html (Ansible notify and Handlers)

Template: (copy from https://github.com/dmccuk/ansible_nginx/blob/master/templates/load-balancer.j2)


### Chapter 8 - Configure GitLab

https://docs.gitlab.com/omnibus/settings/configuration.html#configuring-the-external-url-for-gitlab

### Chapter 10 - Jenkins Server

https://jenkins.io/
What is CI/CD:
(source: https://www.atlassian.com/continuous-delivery/principles/continuous-integration-vs-delivery-vs-deployment)
https://dev.to/bugfenderapp/what-is-jenkins-and-why-should-you-be-using-it-2pe

### Chapter 11 – GitLab and Jenkins Integration 
No links

### Chapter 12 – ServerSpec Infrastructure Testing

https://github.com/dmccuk/spec-tests

### Chapter 13 – Integrate ServersSpec with Jenkins
No links

### Chapter 14 – Elastic Stack + Beats

https://www.elastic.co/products/
https://github.com/dmccuk/ansible_ELK
https://galaxy.ansible.com/docs/contributing/creating_role.html
https://serverspec.org/resource_types.html

## Follow us on LinkedIn:

https://www.linkedin.com/company/londoniac

## Join the LondonIAC Meetup:

http://bit.ly/2Fj7t8M

## Visit our Webpage

www.londoniac.co.uk


