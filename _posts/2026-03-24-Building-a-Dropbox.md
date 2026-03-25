---
title: "Building a Dropbox with a Rasberry Pi"
description: "This is my guide on building a pentesting dropbox with a Rasberry Pi 4."
date: 2026-03-24 00:00:00 +0800
categories: [Pentesting, Rasberry Pi]
tags: [penetration-testing, cybersecurity, red-team, hardware]
---

# Building a Pen Testing Drop Box with a Raspberry Pi 4

## What is a drop box and why would you want one?

A drop box is a small device used by penetration testers to assess the security of an internal network. I use mine for internal network testing as well as Wi-Fi audits using tools like `aircrack-ng` and `kismet`.

There are plenty of alternatives out there - everything from commercial implants to on-site testing or VPN access into a network. However, a drop box offers a flexible, low-cost, and highly portable solution.

For me, the real driver behind building one was the ability to perform **remote Wi-Fi audits**. Not all clients are close enough for a site visit, so having a deployable device is incredibly useful.

Plus, building your own kit is very much in the spirit of hacker culture - hands-on, practical, and a great way to deepen your understanding.

> ⚠️ **Disclaimer:** Use this knowledge responsibly and only for authorised, legal testing.

---

## Requirements

When designing a drop box, I had a few key requirements:

- **Secure by default**  
  We don’t want to introduce new vulnerabilities into a client’s environment.

- **Cost-effective**  
  It should be cheap enough to replace if needed.

- **Easy to deploy**  
  Ideally plug-and-play for the client - no manual setup required onsite.

- **Functional**  
  Must support common penetration testing tools.

- **Wi-Fi capable**  
  Monitor mode support is essential for wireless auditing.

---

## Build List

### Hardware

- **Raspberry Pi 4B (4GB RAM)**  
  You could use a Pi 5, but the 4B is more cost-effective and does the job well.

- **64GB microSD card**

- **Raspberry Pi case**  
  I personally like the Geekworm cases.

- **BrosTrend 650Mbps Linux Wi-Fi Adapter**  
  Reliable with a solid antenna for monitoring.

- **USB power supply**  
  Use a proper wall adapter - not a power bank.

- **MicroSD card reader**

#### Optional:
- HDMI to micro-HDMI cable
- USB keyboard and mouse (for local setup)

---

### Software

- **balenaEtcher** – for flashing the OS  
- **Kali Linux (Raspberry Pi version)**  
- **BrosTrend Wi-Fi drivers**  
- **Tailscale (VPN client)**  

---

## Why Tailscale?

Tailscale is a game-changer for this setup.

It allows you to create a secure, software-defined network using Tailscan, with simple authentication via providers like Google or Microsoft.

Key benefits:
- Easy setup (no complex VPN configs)
- Magic DNS (access devices by name)
- Free tier (up to 100 devices)

Compared to setting up OpenVPN or WireGuard manually, it’s far simpler and quicker.

---

## Setup

I’ll assume you already know how to:
- Flash Kali Linux to the SD card
- Log into the Pi

### Initial Setup Steps

```bash
# Change default password
passwd

# Disable SSH (we'll use Tailscale instead)
sudo systemctl stop ssh
sudo systemctl disable ssh

# Update system
sudo apt update
sudo apt upgrade -y
sudo apt autoremove -y

# Set Hostname
Edit:
/etc/hostname
/etc/hosts

# Reboot.

# Install Wi-Fi Drivers
sh -c 'wget linux.brostrend.com/install -O /tmp/install && sh /tmp/install'

#Install Tailscale
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up --ssh
```
# Clean Up
- Remove saved Wi-Fi networks
- Clear browser history and saved sessions
- Post-Install Hardening

Some additional steps worth considering:

- Enable automatic updates
- Configure log rotation
- Add shell logging via .zshrc
- Use a custom tmux config

# Disable Key Expiry in Tailscale

In the admin console:

- Find your device
- Open the menu (...)
- Select Disable Key Expiry

This ensures the device stays connected after deployment.

# Deployment

Once the device is ready:

- Plug in the USB Wi-Fi adapter
- Connect Ethernet to the local network
- Power on the device
- Then remotely connect via tailscale ssh

# Usage

With the drop box online, you can:

- Audit port security and network segmentation
- Perform Wi-Fi audits (aircrack-ng, kismet)
- Run network scans (nmap)
- Use it as a pivot point into the internal network

If needed, configure Tailscale subnet routing to access the broader network.

# Conclusion

A drop box can significantly enhance your capabilities as a penetration tester or red teamer. Having a device inside a network - whether openly deployed or discreetly placed - gives you a powerful vantage point.

This setup is intentionally simple, but highly flexible. You can customise and harden it further to suit your workflow.

If you’re getting into offensive security, building one of these is a great practical project.

This is just a starting point. Tweak it, break it, improve it - that’s how you learn.
