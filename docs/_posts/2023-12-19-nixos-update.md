---
title: "Updating NixOS packages"
author: "Samuel Kriikkula"
---

Hello there! Today I will show you how to update NixOS to the latest version.

# Update NixOS
First, check what channel you are currently using.
```bash
$ sudo nix-channel --list
nixos https://nixos.org/channels/nixos-23.05
```

Secondly, check if a new version is available [here](https://channels.nixos.org/).
If there is, for example a nixos-24.05, a newer version that is. (larger is better, but be careful if using the unstable channel).
If so, use these commands
```bash
sudo nix-channel --add https://nixos.org/channels/nixos-23.11 nixos # new version
sudo nix-channel --update
sudo nixos-rebuild switch --upgrade
```
