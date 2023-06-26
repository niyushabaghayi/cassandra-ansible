<img width="400px" src="image/cassandra.png">

# Install Apache Cassandra cluster by Ansible

## Prerequisites

Make sure you have installed [python3](https://www.python.org/downloads/), [pip](https://pip.pypa.io/en/stable/installation/) and [ansible](https://pypi.org/project/ansible/) on your host machine.

## Install Apache Cassandra Cluster

In order to install Apache Cassandra cluster on your nodes, it is required to do the following steps.
1. Set global environment variables which are located at `inventory/group_vars/all.yaml` file. For example `cassandra_installation_path` variable indicates that where to keep manifest of docker compose file for Apache Cassandra components.

2. Create `inventory/inventory.yaml` file from the `inventory/inventory.yaml.sample` file and place the `IP` and `user` of the nodes there. You can easily create a new name and place it in inventory.yaml‍ file.


3. Then go to the roles and set the values of each variable on `defaults` directory of each role. For example, you can change the port, by changing the `cassandra_port` value located in `roles/cassandra/defaults/main.yaml` file.

4. Execute the following command:
  ```bash
  ansible-playbook -i <path-to-inventory-file> cluster.yaml -e ansible_ssh_port=8822 -v -b -kK
  # e.g.
  ansible-playbook -i inventory/inventory.yaml cluster.yaml -e ansible_ssh_port=8822 -v -b -kK
  ```

## Start the Cluster
```bash
ansible-playbook -i inventory/inventory.yaml start.yaml -e ansible_ssh_port=8822 -v -b -kK
```
## Remove Apache Cassandra
```bash
ansible-playbook -i inventory/inventory.yaml remove.yaml -e ansible_ssh_port=8822 -v -b -kK
```
# Jobs to be done

- [X] Setup new cluster
- [ ] Add password vault 
- [ ] Setup monitoring with Grafana and Prometheus
- [ ] Persist data of Grafana 
