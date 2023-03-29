Role Name
=========

This role onboard Kubernetes cluster to Azure Arc

Requirements
------------

This role begins with a suitable Kubernetes cluster already created.  In addition, it uses the Azure CLI of the workstation running Ansible to run the *az connectedk8s connect* command to onboard the cluster.  The Azure CLI must be authenticated and the user must have suitable permission for onboarding the cluster.

Role Variables
--------------

This role requires variables to be defined for the following:

- azure_arc.resource_group <-- the Azure resource group that the cluster is to be onboarded to
- azure_arc.location <-- the Azure region where the cluster is to be onboarded

Dependencies
------------

This role has no Galaxy dependencies but can, as illustrated below, be used after the Kubernetes cluster is provisioned, like what can be done with *istvano.microk8s*

Example Playbook
----------------

```
- hosts: arck8s
  roles:
    - role: istvano.microk8s
      vars:
        users: ['jonedoe']
        microk8s_dns_resolvers: 1.2.3.4
        microk8s_plugins:
          dns: "1.2.3.4"
          rbac: true
          storage: true
          helm3: true
    - role: /path/to/role/roles/mrhoads.azure-arc-k8s

```

License
-------

BSD

Author Information
------------------

Mike Rhoads


