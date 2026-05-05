# Private and Public IP Addressing

![Private and Public IP Addressing](https://private-us-east-1.manuscdn.com/sessionFile/PELdhIFr8k4l8jvbPIIMbc/sandbox/aYxk5uAwRLLxbEoe3HlKhb-images_1778005339226_na1fn_L2hvbWUvdWJ1bnR1L2F6dXJlX25ldHdvcmtpbmdfZGlhZ3JhbXMvaW1hZ2VzL3ByaXZhdGUtcHVibGljLWlwLWFkZHJlc3Npbmc.png?Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9wcml2YXRlLXVzLWVhc3QtMS5tYW51c2Nkbi5jb20vc2Vzc2lvbkZpbGUvUEVMZGhJRnI4azRsOGp2YlBJSU1iYy9zYW5kYm94L2FZeGs1dUF3UkxMeGJFb2UzSGxLaGItaW1hZ2VzXzE3NzgwMDUzMzkyMjZfbmExZm5fTDJodmJXVXZkV0oxYm5SMUwyRjZkWEpsWDI1bGRIZHZjbXRwYm1kZlpHbGhaM0poYlhNdmFXMWhaMlZ6TDNCeWFYWmhkR1V0Y0hWaWJHbGpMV2x3TFdGa1pISmxjM05wYm1jLnBuZyIsIkNvbmRpdGlvbiI6eyJEYXRlTGVzc1RoYW4iOnsiQVdTOkVwb2NoVGltZSI6MTc5ODc2MTYwMH19fV19&Key-Pair-Id=K2HSFNDJXOU9YS&Signature=cZ2ozU41Ha8qHJoQpXfzjY0CXGYLxL7VgzMXiDq-SEsIrWhSApw9Px5XXUvWq~h-Q2~c-N9jO4Qx6I1YvMYZXjuexF4d7qOu39Z33xvs4u8RLqBhrIIVgEzkdM4Pn-abcPrqSC734v9zH01YizPgKMzVGxxF4-54ShNTH5kXm~ane6wpe4hlvC0ZUNsE3RaZQyiM4y8VdKvHX-1C5yKW86kzyLiWlMuADTrvybnEAgvE1oIQ00ZtRW1ogdDszz9DqVCergcc1TwLy29FhVstVOiqeaqG3RlhAWqlL9tK-4Rl1nVGxZh8jmkYqZh6ZxV6Qt987HluMOQdvL2YogC3gA__)

## Overview

Understanding the distinction between Private and Public IP addresses is fundamental to networking, both on-premises and in the cloud. This diagram clearly illustrates how devices within a local network communicate with each other using private IPs, and how they utilize Network Address Translation (NAT) to access the global Internet using a single public IP.

This concept is the bedrock of IPv4 network design, allowing millions of private networks to exist without exhausting the limited pool of public IPv4 addresses.

> **Master networking fundamentals on [Cloud360](https://cloud360.co) and watch our IP addressing tutorials on the [Cloud360 YouTube Channel](https://www.youtube.com/channel/UCs005hN86JSDg4PghrhZVjg).**

---

## 1. The Private Network (Local)

The left side of the diagram represents a typical Private Network (LAN), such as a home, office, or enterprise environment.

### Private IP Addresses
Every device connected to this local network is assigned a **Private IP address**. In the example:
- Laptop: `192.168.1.10`
- Smartphone: `192.168.1.11`
- Printer: `10.0.0.25`
- Smart TV: `172.16.0.8`

These addresses are strictly for internal communication. The laptop can talk to the printer using these IPs, but these addresses are **not routable on the public Internet**. Because they are not globally unique, the exact same IP address (e.g., `192.168.1.10`) can be used simultaneously in millions of different private networks around the world.

---

## 2. The Router and NAT (The Bridge)

The central component is the **Router / Firewall**, which acts as the bridge between the private network and the public internet.

### Network Address Translation (NAT)
When a device on the private network (e.g., the Laptop at `192.168.1.10`) wants to access a website, it sends a packet to the router. The router performs **Network Address Translation (NAT)**. 

1. **Outgoing Packet**: The router intercepts the packet, removes the private source IP (`192.168.1.10`), and replaces it with its own Public IP address (`203.0.113.25`). It keeps track of this translation in a NAT table.
2. **Incoming Reply**: When the web server responds, it sends the reply back to the router's Public IP (`203.0.113.25`). The router checks its NAT table, finds the original private IP that made the request, replaces the destination IP, and forwards the packet back to the Laptop (`192.168.1.10`).

NAT is the crucial mechanism that allows many devices with private IPs to share a single public IP to access the Internet.

---

## 3. The Public Internet

The right side of the diagram represents the global, public Internet.

### Public IP Addresses
To communicate on the Internet, a device must have a **Public IP address**. These addresses are globally unique and are assigned by Internet Service Providers (ISPs). 
- The Router's WAN interface has the Public IP: `203.0.113.25`
- The destination Web Server has the Public IP: `198.51.100.10`

Because public IPs are unique, routers across the globe know exactly how to forward traffic to reach them.

---

## 4. Private vs Public IPs: Key Differences

The bottom section provides a clear comparison and defines the specific ranges reserved for private use.

| Feature | Private IPs | Public IPs |
|---------|-------------|------------|
| **Usage Scope** | Used inside local networks (home, office, enterprise). | Globally unique and reachable on the Internet. |
| **Routability** | Not routable on the public Internet. | Used by websites, servers, and Internet services. |
| **Uniqueness** | Can be reused in many different networks. | Must be unique across the entire Internet. |
| **Assignment** | Assigned by local routers/DHCP servers. | Assigned by ISPs (Internet Service Providers). |

### Private IP Address Ranges (IPv4)
The Internet Assigned Numbers Authority (IANA) reserved three specific blocks of IP addresses exclusively for private networks (defined in RFC 1918):
- **10.0.0.0/8**: `10.0.0.0` to `10.255.255.255` (Large enterprise networks)
- **172.16.0.0/12**: `172.16.0.0` to `172.31.255.255` (Medium-sized networks)
- **192.168.0.0/16**: `192.168.0.0` to `192.168.255.255` (Small office/home networks)

---

## Exam Relevance (AZ-104, AZ-700, CompTIA Network+)

For networking and cloud certification exams, this knowledge is foundational:

- **VNet Design**: When creating an Azure Virtual Network (VNet) or AWS VPC, you **must** use Private IP address ranges (RFC 1918). You cannot use public IPs for your internal VNet address space.
- **NAT Gateway**: Understand how managed NAT services (like Azure NAT Gateway) provide outbound internet connectivity for virtual machines that only have private IPs.
- **Public IP Resources**: Know when to assign a Public IP resource to a VM, Load Balancer, or Application Gateway to make it accessible from the internet.

> **Ready to design scalable cloud networks? Visit [Cloud360](https://cloud360.co) for expert architectural guidance and subscribe to the [Cloud360 YouTube Channel](https://www.youtube.com/channel/UCs005hN86JSDg4PghrhZVjg) for practical implementation tutorials.**
