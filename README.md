# Demo Ansible role to manage Podman + Quadlet container application.

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