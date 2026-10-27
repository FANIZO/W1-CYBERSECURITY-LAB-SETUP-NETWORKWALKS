# Week 1: Cybersecurity Lab Environment Setup

## 1. Overview

This project documents the setup and configuration of a cybersecurity lab environment using Kali Linux and Oracle VirtualBox. The lab provides a virtualized environment for learning Linux administration, networking fundamentals, and cybersecurity concepts in a controlled and isolated environment.

The setup includes a Kali Linux virtual machine, VirtualBox network configuration, static IP addressing, connectivity verification, and documentation of the setup process.

## 2. Objectives

The objectives of this lab are to:

- Install and configure Kali Linux in Oracle VirtualBox.
- Understand the basic configuration of a virtual machine.
- Configure a VirtualBox NAT Network.
- Configure static IP addressing, a default gateway, and DNS.
- Verify network connectivity using Linux networking commands.
- Troubleshoot common virtual machine and network configuration issues.
- Maintain screenshots as evidence of the completed lab.
- Establish a baseline virtual machine state for future cybersecurity exercises.

## 3. Lab Environment

| Component | Configuration |
|---|---|
| Host operating system | Windows [confirm version] |
| Virtualization software | Oracle VirtualBox [confirm version] |
| Guest operating system | Kali Linux [confirm version] |
| Virtual network type | NAT Network |
| Network prefix | `10.0.0.0/24` |
| Kali IPv4 address | `10.0.0.2/24` |
| Default gateway | `10.0.0.1` |
| DNS server | `10.0.0.1` |
| DHCP | Enabled on the VirtualBox NAT Network [verify] |

**Note:** The Kali guest was configured with a static IPv4 address. Confirm that the settings above match the final working configuration before publishing this report.

## 4. Network Design

The lab uses a VirtualBox NAT Network to provide network connectivity to the Kali virtual machine.

The configured network uses the `10.0.0.0/24` IPv4 subnet. The Kali virtual machine is assigned the address `10.0.0.2`, with `10.0.0.1` configured as its gateway and DNS server.

| Network setting | Value |
|---|---|
| Network address | `10.0.0.0/24` |
| Kali address | `10.0.0.2` |
| Gateway | `10.0.0.1` |
| DNS server | `10.0.0.1` |
| Subnet mask | `255.255.255.0` |

The NAT Network allows the virtual machine to use the host computer's network connection through VirtualBox. It does not mean the Kali guest is connected to Wi-Fi directly through a physical wireless adapter.

## 5. Setup Procedure

### Step 1: Prepare the virtualization environment

1. Install or open Oracle VirtualBox.
2. Obtain the Kali Linux VirtualBox image from the official Kali Linux website.
3. Import or open the Kali virtual machine.
4. Review the virtual machine's memory, display, storage, and network settings.
5. Start the virtual machine and log in to Kali Linux.

### Step 2: Configure the VirtualBox network

1. Open VirtualBox's network settings.
2. Create or select the NAT Network for the lab.
3. Configure the network prefix as `10.0.0.0/24`.
4. Review the DHCP configuration.
5. Open the Kali VM's network settings and attach its network adapter to the intended NAT Network.
6. Start Kali Linux and verify the guest network configuration.

### Step 3: Configure the Kali network interface

The Kali network interface was configured with the intended static IPv4 settings:

- IP address: `10.0.0.2/24`
- Gateway: `10.0.0.1`
- DNS server: `10.0.0.1`

The NetworkManager connection settings were used to configure the network interface. The actual interface and connection profile should be verified on the running virtual machine.

### Step 4: Verify the configuration

The following commands can be used to inspect the configuration:

```bash
ip -4 addr show eth0
ip route
cat /etc/resolv.conf
```

These commands show the IPv4 address, routing table, and configured DNS resolver information.

### Step 5: Verify connectivity

The following tests can be used to verify network connectivity:

```bash
ping -c 4 10.0.0.1
ping -c 4 1.1.1.1
getent hosts google.com
```

The first test checks reachability of the configured gateway. The second checks connectivity to an external IP address. The third checks whether the system can resolve a domain name through DNS.

Successful results should be recorded with screenshots. If any test fails, document the actual result rather than marking it as successful.

### Step 6: Prepare the environment for future labs

After confirming the setup, review the VM configuration and save evidence of the working environment. A VirtualBox snapshot can be created as a recovery point before later lab exercises.

## 6. Troubleshooting and Lessons Learned

During the setup, troubleshooting was required to resolve configuration issues and improve the usability of the virtual machine.

### Network connectivity

The network interface and static IP settings were checked using Linux networking commands and VirtualBox network settings. The NAT Network attachment and NetworkManager connection configuration were reviewed to restore connectivity.

### Display and Guest Additions

The full-screen display and guest integration features were investigated. The troubleshooting process included reviewing the `virtualbox-guest-x11` and `virtualbox-guest-utils` packages and checking the `vboxguest` kernel module.

These checks helped distinguish between a package installation issue and a kernel driver or device integration issue.

**Final status:** [Record the final verified status of full-screen resizing, clipboard sharing, and drag-and-drop.]

## 7. Evidence

Screenshots are stored in the `screenshots/` directory.

| Screenshot | Evidence |
|---|---|
| `01-virtualbox-kali-vm.png` | Kali Linux virtual machine running in VirtualBox |
| `02-nat-network-settings.png` | NAT Network configuration |
| `03-kali-desktop.png` | Kali Linux desktop |
| `04-network-configuration.png` | IPv4 address and routing table |
| `05-connectivity-tests.png` | Gateway, external IP, and DNS verification |
| `06-vm-snapshot.png` | VirtualBox snapshot, if created |

## 8. Learning Outcomes

By completing this lab, I practised:

- Setting up a virtualized Linux environment.
- Understanding the relationship between a host operating system and a guest virtual machine.
- Configuring IPv4 addresses, gateways, DNS, and virtual networking.
- Using Linux commands to inspect network interfaces and routing.
- Troubleshooting network and virtual machine integration issues.
- Recording technical work with screenshots and version-controlled documentation.

These skills provide a foundation for subsequent networking, system administration, and cybersecurity labs.

## 10. References

- Kali Linux: https://www.kali.org/
- Kali Linux VirtualBox installation guidance: https://www.kali.org/docs/virtualization/install-virtualbox-guest-vm/
- Oracle VirtualBox documentation: https://www.virtualbox.org/manual/
- GitHub Markdown documentation: https://docs.github.com/en/get-started/writing-on-github
