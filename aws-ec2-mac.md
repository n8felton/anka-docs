---
title: "Anka on AWS EC2 Macs"
linkTitle: "Anka on AWS EC2 Macs"
weight: 3
date: 2017-01-20
description: >
  Up and running fast, with Anka and Amazon (AWS) EC2 Macs
aliases:
  - /intel/getting-started/aws-ec2-mac/
---

{{< hint info >}}
This guide is also valid for the Anka 3/mac2.metal/Apple processor (M1, M2, etc) EC2 instances.
{{< /hint >}}

Customers often find that purchasing and managing their own hardware can become a burden. This is why we recommend using AWS EC2 Mac instances to run the Anka Virtualization software.

With Anka installed on your AWS EC2 Mac instance, you can run ephemeral macOS VMs as well as optimize the instance cost by running more than one at a time. [Visit our site](https://veertu.com/aws-ec2-mac/) and [Amazon's blog](https://aws.amazon.com/blogs/compute/getting-started-with-anka-on-ec2-mac-instances/) for more information about AWS EC2 Mac and Anka.

---

There are three options available for you to use Anka with AWS EC2 Mac instances:

1. [**Use our Marketplace AMI**]({{< relref "#marketplace-ami" >}})
  - macOs pre-configured/optimized + Anka installed
  - Provides an hourly billing option for Anka based on the uptime of your EC2 Mac instance
2. [**Bring your own license (BYOL) Community AMI**]({{< relref "#community-ami" >}})
  - macOS pre-configured/optimized + Anka installed
  - With these AMIs, you will be able to use your own Anka License.
3. [**Build your own AMI**]({{< relref "#build-your-own-ami" >}})

{{< hint info >}}
Note: You must request a dedicated mac* host in order to run EC2 Mac instances. There is a known delay requesting, stopping, and starting EC2 Mac instances as the dedicated host must clean itself each time an instance stops on it.
{{< /hint >}}

---

## Marketplace AMI

In order to get started using our Marketplace AMIs you have four options:

1. Intel + Basic License : [Product Page](https://aws.amazon.com/marketplace/pp/prodview-tzmid5kfn2knw)
2. Intel + Enterprise License : [Product Page](https://aws.amazon.com/marketplace/pp/prodview-rp7kfyl56arbe)

Other than the hourly price, there is [a list of features that differ between the two.]({{< relref "licensing.md#anka-build-cloud" >}})

{{< hint info >}}
You can find a full list of products available on the AWS marketplace by visiting https://veertu.com/aws-marketplace. Or, once subscribed, you can find and launch instances from the marketplace AMIs on the [Manage Subscriptions page](https://console.aws.amazon.com/marketplace/home/subscriptions?#/subscriptions).
{{< /hint >}}

{{< hint info >}}
Marketplace AMIs are charged on an hourly basis and don't need an Anka License.
{{< /hint >}}

{{< hint info >}}
You can create custom AMIs from the Marketplace AMI and the license for Anka will continue to work and attach to your existing marketplace subscription.
{{< /hint >}}

### Usage

To get up and running with our AWS EC2 Mac instances using our Marketplace AMI, you'll need to navigate to one of the Marketplace AMI Product URLs listed above and go through the process of subscribing. [Take a look at the official AMI Subscription documentation to understand how to subscribe.](https://docs.aws.amazon.com/marketplace/latest/buyerguide/buyer-ami-subscriptions.html)

Once subscribed, you can start launching AMIs.

{{< include file="_partials/ec2-mac-amis/prep-steps.md" >}}

#### Licensing

The Marketplace AMI does not require a license. You are charged hourly for the usage through [the AWS marketplace](https://docs.aws.amazon.com/marketplace/latest/userguide/pricing.html). Anka marketplace AMIs are available with Anka Basic and Anka Enterprise Tier features. For more details on Basic and Enterprise Tier, [check out our documention.]({{< relref "licensing.md#anka-build-cloud" >}})

### Anka Build Cloud automated setup scripts

We have a script that will set up both a Linux instance with the [Anka Build Cloud Controller & Registry](https://veertu.com/anka-build/). You can find it under our [Getting Started repo’s AWS folder](https://github.com/veertuinc/getting-started#aws-aws).

1. Clone the getting-started repo

    ```bash
    git clone https://github.com/veertuinc/getting-started.git
    cd getting-started
    ```

2. Execute [`./AWS/prepare-build-cloud.bash`](https://github.com/veertuinc/getting-started#prepare-build-cloudbash)
    - Running this script will create everything necessary inside of AWS to run the Anka Build Cloud. This includes a security group, elastic IP, etc.

The script can be run locally from your local macOS laptop with an existing AWS credential, region set, etc. These scripts have not been tested on linux.

---

## Community AMI

Our BYOL Community AMIs are useful if you'd like to bring your own existing Anka license. They both have all of the same configuration changes, optimizations, and Anka inside. The difference is that Anka is unlicensed.

You can find a list of currently available Community AMIs below:

{{< include file="_partials/ec2-mac-amis/community-ami-list.md" >}}

### Usage

To get up and running with our AWS EC2 Mac instances using our BYOL Community AMI, you'll need to:

1. Have an AWS mac1 (intel) or mac2 (arm/apple/m1) dedicated host ready.

2. Have an [Anka license](https://veertu.com/anka-build-trial/).

3. Choose the Community AMI when starting an instance:
  {{< imgwithlink src="images/getting-started/aws-ec2-mac/aws-choose-ami.png" >}}

{{< include file="_partials/intel/Getting Started/ec2-mac-amis/prep-steps.md" >}}



#### Licensing

When you first license Anka, keep track of the fulfillment ID as you'll need this to release the cores and use the license on a fresh machine.

{{< hint info >}}
The Anka Develop license type will not work on AWS EC2 Macs.
{{< /hint >}}

{{< hint info >}}
Stopping and starting the instance does not impact the Anka licenses validity, even if you start the instance on a different dedicated machine.
{{< /hint >}}

{{< hint warning >}}
Before terminating an instance, you will need to remove the Anka license first and then contact Veertu support (support@veertu.com) to clear the fulfillments
{{< /hint >}}

### Anka Build Cloud automated setup scripts

We have two scripts that will set up both a Linux instance with the [Anka Build Cloud Controller & Registry](https://veertu.com/anka-build/) as well as an EC2 Mac instance (Anka Node) to run VMs. This relies on our Community AMI and you will need to have an Anka License. You can find them under our [Getting Started repo’s AWS folder](https://github.com/veertuinc/getting-started#aws-aws).

1. Clone the getting-started repo

    ```bash
    git clone https://github.com/veertuinc/getting-started.git
    cd getting-started
    ```

2. Execute [`./AWS/prepare-build-cloud.bash`](https://github.com/veertuinc/getting-started#prepare-build-cloudbash)
    - Running this script will create everything necessary inside of AWS to run the Anka Build Cloud. This includes a security group, elastic IP, etc.

3. Execute [`./AWS/prepare-anka-node.bash`](https://github.com/veertuinc/getting-started#prepare-anka-nodebash)

    - Requires that you first run `prepare-build-cloud.bash`.

    - Running this script will create everything necessary inside of AWS to run an EC2 Mac instance. You’ll be prompted for the Anka license to use if the ANKA_LICENSE env variable is not set.

Both scripts can be run locally from your local macOS laptop with an existing AWS credential, region set, etc. These scripts have not been tested on linux.

---

## Build your own AMI

Building your own AMI is easy! You can review our [AMI scripts](https://github.com/veertuinc/aws-ec2-mac-amis) to see how we do it.

Some important notes about creating your own AMI:

- Be sure that the minimum EBS volume specs are gp3, 6000IOPS, and 256 throughput. Anka VM creation is sensitive on slow disks and will likely fail.

---
