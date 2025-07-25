# Demo Ansible role to manage Podman + Quadlet container application.

This repo is used to demostrate some of the Podman+Quadlet functionality when using native k8s YAML to run define systemd services.
The Ansible role included is designed to work on RHEL9/Alma9 machines.

## Instructions:

1. add appropriate machine details to inventory.ini
2. run ansible command:
`ansible-playbook -i inventory.ini main.yml`

Note: The opencanary config for this demo is meaningless and is just there to get the container running.

## Handy commands:

### switch to canary user
`machinectl shell --uid canary`

### check status of service as canary user
`systemctl status --user canary.service`

## show journal logs of service as canary user
`journalctl --user -u canary.service`

### show podman inspect state.health
`podman inspect opencanary-opencanary1 | jq .[0].State.Health`
 
### show restart counter for container
`podman inspect opencanary-opencanary1 | jq .[0].RestartCount`
 
### show health check config for container
`podman inspect opencanary-opencanary1 | jq .[0].Config.Healthcheck`