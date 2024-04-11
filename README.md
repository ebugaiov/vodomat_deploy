# vodomat_deploy

### Vodomat_deploy is a bunch of scripts deploying vodomat services to production.
### There are two git branches:
- main: for production deploy
- dev: for local deploy
### Check in vault file several variables before deploy in production environment:
- sudo_user
- vodomat_server_hostname
- vodomat_hub_hostname
- server_url
- api_url
- admin_server_url

# How to use
### 1. Server - deploy server services (server.yml):
 - vodomat_server

#### - Setup instance(install docker and etc.):
```bash
ansible-playbook -i inventory.ini server.yml -K --tags "preconfig"
```

#### - Run reverse-proxy (Traefik)
```bash
ansible-playbook -i inventory.ini server.yml --tags "run_proxy"
```

#### - Deploy vodomat_server service
```bash
ansible-playbook -i inventory.ini server.yml --tags "deploy_server"
```

-------

### 2. Hub - deploy hub services (hub.yml):
 - vodomat_api
 - vodomat_server_admin

#### - Setup instance(install docker and etc.):
```bash
ansible-playbook -i inventory.ini hub.yml -K --tags "preconfig"
```

#### - Run reverse-proxy (Traefik)
```bash
ansible-playbook -i inventory.ini hub.yml --tags "run_proxy"
```

#### - Deploy ALL services
```bash
ansible-playbook -i inventory.ini hub.yml -K --tags "deploy_all"
```

#### - Deploy vodomat_api service
```bash
ansible-playbook -i inventory.ini hub.yml --tags "deploy_api"
```

#### - Deploy vodomat_server_admin service
```bash
ansible-playbook -i inventory.ini hub.yml -K --tags "deploy_server_admin"
```
--------
-K - enter sudo password
