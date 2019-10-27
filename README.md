# concourse-ansible
Run ansible script from concourse job

This is the dockerfile for captainstuart/ansible-playbook

It is for use in concourse to run ansible jobs from a task.

Adapted from: https://github.com/walokra/docker-ansible-playbook/blob/master/Dockerfile

###Example usage in concourse job

```
  - task: Update_L2
    config:
      platform: linux
      image_resource:
        type: docker-image
        source:
          repository: captainstuart/ansible-playbook
          tag: "2.0"
      inputs:
      - name: network
      - name: vars
      run:
        path: ansible-playbook
        dir: network
        args:
        - switch.yaml
        - --vault-password-file=../vars/vault_password
```

 