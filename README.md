# Training on Kubernetes

## Installation

### Prerequisites

* Four AWS EC2 nodes, in the same subnetwork.
* Download your private key to be able to access the nodes.
* CentOS 7 installed on them. I've  used the `dcos-centos7-201703311845 (ami-7dcd1d12)` AMI.
* Allow connections to ICMP and all TCP/UDP ports for the private IP subnetwork.

### Configuration

# Start by configuring the `hosts` file, by adding your EC2 instances public IPs.
# Next, edit the `Roles/setup.minions/vars/main.yml` and add there the private IPs of your nodes.

### Installation

Install everything by executing:

```
ansible-playbook prerequisites.yml install-master.yml install.minions.yml
```

Check the state of the nodes:

```
ansible master -ucentos -mshell -a"kubectl get nodes"
```

They should all be Ready.

### Clean up

Clean up everything by executing:

```
ansible-playbook uninstall.yml
```

Profit!
