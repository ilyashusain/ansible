# ansible

Below we will look at an instance within my code where we install jenkins by on to a vm by means of a .yml file. Outline of methodology:

```bash
- hosts: 10.142.0.9
```
This is the internal IP of the VM where we install jenkins.
```bash
  tasks:
  - name: Set-up java
    yum:
      name: java
    become: true
```
In this tasks block, we install java. The module is ```bash yum```. The ```bash become: true``` command allows us to assume a sudo permissions.
```bash
  - name: Set-up wget
    yum:
      name: wget
    become: true
```
Same as above, but we install wget.
```bash
  - name: Set-up wget jenkins
    shell:
      sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
```
In this block, we use the very useful ```bash shell``` module. It allows us to implement lines of code as if we were in the shell.
```bash
  - name: Set-up rpm jenkins
    shell:
      sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
```
Another shell command, familiar to any who regularly installs jenkins.
```bash
  - name: Set-up jenkins
    shell:
      sudo yum install -y jenkins
    become: true
```
In this block, we install jenkins by means of a shell command. There is no specific jenkins module, so the shell command proves useful.
