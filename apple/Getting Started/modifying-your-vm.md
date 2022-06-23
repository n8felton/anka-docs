---
title: "Modifying your VM"
linkTitle: "Modifying your VM"
weight: 4
description: >
  Modify your VM using the Anka Virtualization CLI
---

## Prerequisites

1. [You've installed the Anka Virtualization package]({{< relref "apple/Getting Started/installing-the-anka-virtualization-package.md" >}})
2. [You've created your first VM]({{< relref "apple/Getting Started/creating-your-first-vm.md" >}})

---

{{< hint warning >}}
The rest of this Getting Started guide focuses heavily on the (Command-Line Interface). These will be performed from within your [macOS Terminal](https://support.apple.com/guide/terminal/welcome/mac). For all available CLI commands, flags, and options, see the [Command Reference]({{< relref "apple/command-line-reference.md" >}}).
{{< /hint >}}

{{< include file="_partials/apple/Anka Virtualization/modify/_index.md" >}}

{{< include file="_partials/apple/Anka Virtualization/modify/set/_index.md" >}}

{{< include file="_partials/apple/Anka Virtualization/modify/disk/_extra.md" >}}

## Common Examples

### Changing your VM's network configuration

Depending on your network topology, there are instances where you might need to use a bridge mode and assign your VM a unique IP address instead of the default shared IP of the host:

{{< include file="_partials/apple/Anka Virtualization/modify/network/_index.md" >}}

{{< include file="_partials/apple/Anka Virtualization/modify/network/_extra.md" >}}

{{< include file="_partials/apple/Anka Virtualization/modify/network/_example.md" >}}

---

## What's next?

- [Understanding VM Networking]({{< relref "apple/Getting Started/understanding-vm-networking.md" >}})