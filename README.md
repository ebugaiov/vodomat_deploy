# vodomat_deploy

Vodomat_deploy is a bunch of scripts deploying vodomat services to production.

# How to use
### 1. Server - deploy server services (server.yml):
 - vodomat_server
 - vodomat_server_admin
 - vodomat_api

#### - Setup instance(install docker and etc.):
```bash
ansible-playbook -i inventory.ini server.yml -K --tags "preconfig"
```
-K - enter sudo password

#### - Deploy vodomat_server service
```bash
ansible-playbook -i inventory.ini server.yml --tags "deploy_server"
``` 
