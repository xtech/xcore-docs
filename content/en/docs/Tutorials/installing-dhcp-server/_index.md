---
title: "Installing and Configuring a DHCP Server"
linkTitle: "Install a DHCP Server"
description: This guide walks you through setting up `isc-dhcp-server` on your xCore board.
---

## Why Set Up a DHCP Server?

The xCore board serves as the central hub in an internal network used by your robot.
The xCore includes a microcontroller (STM32) which talks directly with the Linux system. To enable this, we create a private network on `eth0` with a static IP and assign dynamic IPs to connected devices using DHCP.
The STM32 will acquire an IP address automatically.


---

## Step 1: Set Static IP on `eth0`

We will assign a static IP `172.16.78.1` to `eth0`. You can do this using the built-in network configuration utility:

```bash
sudo nmtui
```

1. Select **Edit a connection**
2. Choose your **Wired connection**
3. Set **IPv4 Configuration** to **Manual**
4. Add:
    - Address: `172.16.78.1`
    - Netmask: `255.255.255.0`
    - Gateway: leave blank
5. Save and **Activate** the connection

> 💡 You may also use `nmcli` instead:
```bash
sudo nmcli con mod "Wired connection 1" ipv4.method manual ipv4.addresses 172.16.78.1/24
sudo nmcli con up "Wired connection 1"
```

Verify the result by running `ip -4 address show dev eth0`.
The expected output should be:
```bash
robot@robot:~ $ ip -4 address show dev eth0
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    inet 172.16.78.1/24 brd 172.16.78.255 scope global noprefixroute eth0
       valid_lft forever preferred_lft forever
```

---

## Step 2: Install the DHCP Server

```bash
sudo apt-get update
sudo apt-get install isc-dhcp-server -y
```

---

## Step 3: Configure DHCP Server

### Edit default interface

Open `/etc/default/isc-dhcp-server`:

```bash
sudo nano /etc/default/isc-dhcp-server
```

Find and modify this line:

```bash
INTERFACESv4="eth0"
```

Save the configuration by pressing `CTRL+O`, `ENTER`. Then exit nano by pressing `CTRL+X`.

---

### Add DHCP configuration

Edit the main DHCP config file:

```bash
sudo nano /etc/dhcp/dhcpd.conf
```

Replace the config with the following:

```conf
default-lease-time 600;
max-lease-time 7200;
authoritative;

subnet 172.16.78.0 netmask 255.255.255.0 {
  interface eth0;
  range 172.16.78.150 172.16.78.200;
  option routers 172.16.78.1;
  option domain-name-servers 172.16.78.1;
  option domain-name "robot.local";
}
```

---

## Step 4: Start the DHCP Server

```bash
sudo systemctl start isc-dhcp-server
```

Enable it at boot:

```bash
sudo systemctl enable isc-dhcp-server
```

---

## Verification

Run:

```bash
sudo systemctl status isc-dhcp-server
```

Make sure the output includes `active (running)`.

Try to ping your STM32:
Get the assigned IP by running `cat /var/lib/dhcp/dhcpd.leases`

**Example output:**
```bash
robot@robot:~ $ cat /var/lib/dhcp/dhcpd.leases
# The format of this file is documented in the dhcpd.leases(5) manual page.
# This lease file was written by isc-dhcp-4.4.3-P1

# authoring-byte-order entry is generated, DO NOT DELETE
authoring-byte-order little-endian;

server-duid "\000\001\000\001/\244\342\375,\317gJ\305\345";

lease 172.16.78.150 {
  starts 3 2025/04/30 13:33:05;
  ends 3 2025/04/30 13:43:05;
  cltt 3 2025/04/30 13:33:05;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet d8:47:8f:91:b9:6c;
}
```

Then you should be able to ping the STM32:
```bash
robot@robot:~ $ ping 172.16.78.150
PING 172.16.78.150 (172.16.78.150) 56(84) bytes of data.
64 bytes from 172.16.78.150: icmp_seq=1 ttl=255 time=0.354 ms
```
