# DCICTF 2018 Ansible playbook
Ansible playbook to manage the DCICTF 2018 infrastructure

## Playbooks
Basic description of the different playbooks

### challenges-servers
Provision the hosts with the tools needed to host the different challenges of DCI CTF 2018.
```
❯ ansible-playbook playbooks/challenges-server.yml -u root
```

### challenges
Pull, build and run the different challenges of DCI CTF 2018.
```
❯ ansible-playbook playbooks/challenges.yml -u root
```

### Restarting a specific challenge
All the challenges are tagged by their names. Restarting a challenge is as simple as:
```
❯ ansible-playbook playbooks/challenges.yml -u root --tags "coding1"
```
This will rebuild the image for `coding1` challenge , kill the container of `coding1` (if it's running) and start a new container with the new image of `coding1`. 
