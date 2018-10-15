# DCI CTF 2018 Ansible playbook
Ansible playbook to manage the DCI CTF 2018 infrastructure

Make sure to create an `ansible.cfg` and `dcictf-inventory` file at the root of the repo using the provided template files.

## Playbooks
Basic description of the different ansible playbooks found in this repo.
To launch a playbook, run: 
```
❯ ansible-playbook playbooks/<playbook-name>.yml
```

### authorizations
Setup ssh public keys on the different hosts.

### challenges-servers
Provision the hosts with the tools and dependencies needed to host and run the different challenges of DCI CTF 2018.

### challenges
This playbook defines tasks to build, run and kill the different DCI CTF 2018 challenges on the challenge servers defined in the `challenges` hosts group.

Pull, build and run the different challenges of DCI CTF 2018.
```
❯ ansible-playbook playbooks/challenges.yml
```
Restarting a single challenge is as simple as:
```
❯ ansible-playbook playbooks/challenges.yml --extra-vars "challenge=coding1"
```
This will rebuild the image for `coding1` challenge , kill the container of `coding1` (if it's running) and start a new container with the new image of `coding1`.

To kill all challenge containers, simply run:
```
❯ ansible-playbook playbooks/challenges.yml --tags "kill_challenges"
```

### monitoring
Setup monitoring stack on the challenges-server

### scoreboard-backups
Setup automatic backup of the scoreboard using Amazon S3.

### scoreboard
Provision the scoreboard hosts with the tools needed to run CTFd, then launch CTFd with our configuration.

