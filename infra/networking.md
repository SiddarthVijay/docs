# Networking

Currently when started infra creates 2 docker networks:

* `regnet` - used to host local docker registry from where images are pushed or pulled
* `kiranet` - used to deploy validator nodes and other software relevant to the kira network operations


## RegNet


> Default Subnet: `100.0.0.0/8`
>
> Registry Hostname: `registry.local`
>
> Registry Ip Address: `100.0.1.1`
> 
> Registry Port: `5000`

To test that registry is operational you can run following command within the VM:

```
curl --max-time 3 "100.0.1.1:5000/v2/_catalog"
```

_NOTE: There exists a global environment variable called `KIRA_REGISTRY` that aliases the `registry.local:5000` registry address_

_NOTE: It might happen that as result of VM shutdown, hibernation or other issues registry network stops being responsive, if that happens use the `Hard RESET Repos & Infrastructure` command in the Kira Network Manager which will automatically detect this issue and re-create the network._

## Kira Net

> Default Subnet: `101.0.0.0/8`

Each "Kira Hub" validator deployed within this network has automatically assigned IP address with a following format: `101.1.0.X` where `X` defines the the node identifier.

For example, `validator-1` will have ip `101.1.0.1` assigned to its container while `validator-67` will have ip `101.1.0.67`

The maximum number of validators that can be locally deployed is `254`