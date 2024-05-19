# vodomat_deploy

### Vodomat_deploy is a bunch of scripts deploying vodomat services to production.

# How to use
### 1. Server - deploy server services (server.yml):
 - vodomat_server

#### - Setup instance(install docker and etc.)
```bash
ansible-playbook -i inventory.ini server.yml -K --tags "preconfig"
```

#### - Run reverse-proxy (Traefik)
```bash
ansible-playbook -i inventory.ini server.yml --tags "run_proxy"
```

#### - Run database (MariaDB)
```bash
ansible-playbook -i inventory.ini server.yml --tags "run_database"
```

#### - Deploy vodomat_server service
```bash
ansible-playbook -i inventory.ini server.yml --tags "deploy_server"
```
```bash
ansible-playbook -i inventory.ini server.yml --tags "deploy_server" -e "production=true"
```

-------

### 2. Hub - deploy hub services (hub.yml):
 - vodomat_api
 - vodomat_server_admin

#### - Setup instance(install docker and etc.)
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
```bash
ansible-playbook -i inventory.ini hub.yml --tags "deploy_api" -e "production=true"
```

#### - Deploy vodomat_server_admin service
```bash
ansible-playbook -i inventory.ini hub.yml -K --tags "deploy_server_admin"
```
```bash
ansible-playbook -i inventory.ini hub.yml -K --tags "deploy_server_admin" -e "production=true"
```
--------
### 3. App - deploy vodomat-pay application (app.yml):
 - vodomat_pay_api
 - vodomat_pay_frontend

#### - Setup instance(install docker and etc.)
```bash
ansible-playbook -i inventory.ini app.yml -K --tags "preconfig"
```

#### - Run reverse-proxy (Traefik)
```bash
ansible-playbook -i inventory.ini app.yml --tags "run_proxy"
```

#### - Deploy ALL services
```bash
ansible-playbook -i inventory.ini app.yml --tags "deploy_all"
```

#### - Deploy vodomat_pay_api service
```bash
ansible-playbook -i inventory.ini app.yml --tags "deploy_app_api"
```
```bash
ansible-playbook -i inventory.ini app.yml --tags "deploy_app_api" -e "production=true"
```

#### - Deploy vodomat_pay_frontend service
```bash
ansible-playbook -i inventory.ini app.yml --tags "deploy_app_frontend"
```
```bash
ansible-playbook -i inventory.ini app.yml --tags "deploy_app_frontend" -e "production=true"
```
--------
1. -K - enter sudo password
<br>
2. -e "github_repo_version=xxxxxx" - add in the end of command for specific repo commit
<br>
3. -e "production=true" - deploy services in production environment (default - "false")
