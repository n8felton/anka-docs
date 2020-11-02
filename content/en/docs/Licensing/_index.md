---
date: 2017-08-16T14:27:24-07:00
title: "Licensing"
linkTitle: "Licensing"
weight: 10
description: >
  Detailed information on Anka Licensing
---

Anka licenses are available for the following products:

+ **Anka Build Basic** - All Basic features to configure and run macOS CI Cloud infrastructure
+ **Anka Build Enterprise** - Basic + additional features for grouping, priority provisioning etc
+ **Anka Build Enterprise Plus** - Enterprise + additional features to support SSO, VM encryption, event logging
+ **Anka Flow** - Install and configure Anka on developer mac workstations. Supported only on macbook models and iMac.
+ **Anka Secure** - Install and configure Anka on mac workstations to create secure, sandbox macOS working environments for privileged data access etc

## Anka Build License Tier Datasheet

**Feature** | **Basic** | **Enterprise** | **Enterprise Plus**
--- | --- | --- |  ---
Core based licensing | Yes | Yes | Yes
Cloud Controller with REST APIs | Yes(Single instance of Anka controller included) | Yes(Single instance of Anka controller included) | Yes
Central Registry | Yes(Single instance Anka Registry included) | Yes | Yes
[GitHub Action](https://github.com/marketplace/actions/anka-vm-github-action) | Yes | Yes | Yes
[Jenkins Plugin](https://plugins.jenkins.io/anka-build/) | Yes | Yes | Yes
[TeamCity Plugin](https://plugins.jetbrains.com/plugin/10733-anka-build-cloud) | Yes | Yes | Yes
[GitLab Runner with custom executor](https://github.com/veertuinc/gitlab-runner) | Yes | Yes | Yes
[BuildKite Plugin](https://github.com/veertuinc/anka-buildkite-plugin) | Yes | Yes | Yes
HA for Controller configuration setup | Yes (Additional controller/registry instances needed) | Yes | Yes
[USB Device control through the CLI]({{< relref "docs/Getting Started/working-with-usb-devices.md" >}}) |  Yes  | Yes | Yes
[USB Device control through Controller API]({{< relref "#usb-device-control-controller-api" >}}) |    | Yes | Yes
[Priority scheduling of VMs through controller]({{< relref "#priority-scheduling" >}}) |    | Yes | Yes
[Clustering (Grouping) of Nodes]({{< relref "#node-groups" >}}) |    | Yes | Yes 
[Basic controller authentication (Certificate & Root Superuser Token)]({{< relref "docs/Anka Build Cloud/Controller and Registry/Advanced Security Features/_index.md" >}}) |    | Yes | Yes
[Multi-user & group authorization with admin panel + OpenID/SSO support]({{< relref "docs/Anka Build Cloud/Controller and Registry/Advanced Security Features/openid-authentication.md" >}}) |    |    | Yes
Controller API activity logging |    |    | Yes
VM full disk encryption for Build VMs |    |    | Yes
Control VM runtime (Networking, Access to host) and functional properties with policies |    |    | Yes 

> Feature details can be found [here]({{< relref "docs/Anka Build Cloud/Controller and Registry/license-tiers.md" >}}) 

### Trial License
Trial license for Anka products is valid for 30 days from the date of trial registration. You can use the same activation key on multiple machines (Depending upon the quantity specified at the time of trial registration).  

**Anka Build** Trial licenses are generated with Enterprise entitlement.

Download `anka.pkg` and install it on mac harwdare.

Activate license using `sudo anka license` command to activate the license on each machine with the activation key. The machines should be connected to the internet at the time of activation either directly or through proxy.  

Anka uses standard `http_proxy` and `https_proxy` env variables. `sudo` will not pass the environment by default, so activation should be called with `sudo -E anka license activate ...` to pick up the environment variables.
```
sudo anka license activate <activationkey>
anka license show
```

See remaining cores on your Anka Build license key with this command.

`anka license show -k <Key>`

### Commercial License
Anka licenses are issued for yearly license subscription which includes updates, upgrades and standard support. They can be purchased for a single year or multiple years. 

#### Automatic extension of Commercial License upon renewal
This feature is implemented to eliminate the need for users to manually reactivate license on the Anka nodes upon renewal of their yearly licenses.
Auto extension logic in anka licensing executes once every day and if days to expiration is > 30 days, then no action is taken. If the license is expired, then no action is taken. If days to expiration is < 30 days, then the licensing on the node tries to reactive license with updated license expiration date from the backend licensing service.

### Changing from Trial to Commercial license
First, stop all the running or suspended VMs. Then, remove the old license and activate with the commercial activation key.

```
sudo anka license remove
sudo anka license activate <newactivation key>
```
### Moving your Commercial license from one machine to another
Remove the license from the machine using the below described command.

```
sudo anka license remove
Are you sure you want to remove current license? [y/N]: y
License is removed. To activate with the same activation key on another machine,
contact support@veertu.com with your activation key and fulfillment ID 2727000039

```
Contact [support@veertu.com](mailto:support@veertu.com) with the fulfillment ID provided in the output of the `anka license remove` command and your license key.

### Pricing

+ **Anka Build** - Cost is core based. For example. if you are setting up a cloud consisting of 2, 6-core mac minis, then total core count will be 12 cores.
+ **Anka Flow** - Cost is per machine. For example, if you are installing Anka Flow on 10 developer machines, then quantity will be 10.
+ **Anka Secure** - Cost is per machine. For example, if you are installing Anka Flow on 10 mac workstations, then quantity will be 10.

Contact [support@veertu.com](mailto:support@veertu.com) to get a pricing estimate.  




