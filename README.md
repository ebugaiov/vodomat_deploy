# vodomat_deploy

Vodomat_deploy is a bunch of scripts deploying vodomat services to production.

# How to use
### 1. Server - deploy to swarm cluster (server.yml)

#### - Setup nodes(install docker and etc.):
```bash
ansible-playbook -i inventory/server_cluster.ini server.yml -K --tags "preconfig"
```
-K - enter sudo password<br>
--tags <b>"preconfig"</b>

#### - Init swarm cluster and join nodes to it:
```bash
ansible-playbook -i inventory/server_cluster.ini server.yml --tags "collect_cluster"
```
--tags <b>"collect_cluster"</b>

#### - Build image of service:
```bash
ansible-playbook -i inventory/server_cluster.ini server.yml --tags "build_[service_name]"
```
--tags <b>"build_[service_name]"</b>: all(build all images), vodomat_server, vodomat_server_admin

#### - Deploy service to cluster
```bash
ansible-playbook -i inventory/server_cluster.ini server.yml --tags "deploy_[service_name]"
```
--tags <b>"[service_name]"</b>: all(deploy all services), redis, vodomat_server, 
