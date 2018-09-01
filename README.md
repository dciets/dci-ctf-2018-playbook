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

### restarting a specific challenge
Restarting a single challenge is as simple as:
```
❯ ansible-playbook playbooks/challenges.yml -u root --extra-vars "challenge=coding1"
```
This will rebuild the image for `coding1` challenge , kill the container of `coding1` (if it's running) and start a new container with the new image of `coding1`. 

### scoreboard
Provision the scoreboard hosts with the tools needed to run CTFd, then launch CTFd on those hosts with our configuration.
```
❯ ansible-playbook playbooks/scoreboard.yml -u root
```
