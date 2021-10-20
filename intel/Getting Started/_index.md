---
title: "Getting Started"
linkTitle: "Getting Started"
weight: 2
sidebar_menu_sub_sections_exposed: true
description: >
  A guide for getting started using Anka Virtualization software
---

> One of the most common problems when getting started is the usage of `sudo` for anka commands. Anka will run for all users on a machine, but they will have isolated environments. If you create an Anka VM Template/Tag as UserA, sudo/root will not be able to see or use them. Also, the Anka Build Cloud Controller will start VMs as root, so be sure to clean up any VM Templates and Tags you have under UserA or else the disk space will become a problem. It's suggested to just run all anka commands as root.