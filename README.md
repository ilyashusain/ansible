# ansible

Outline of methodology:

```bash
- hosts: 10.142.0.9
  tasks:
  - name: Set-up java
    yum:
      name: java
    become: true
  - name: Set-up wget
    yum:
      name: wget
    become: true
  - name: Set-up wget jenkins
    shell:
      sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
  - name: Set-up rpm jenkins
    shell:
      sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
  - name: Set-up jenkins
    shell:
      sudo yum install -y jenkins
    become: true
```
