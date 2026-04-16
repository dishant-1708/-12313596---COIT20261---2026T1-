
Below is a **clean Markdown (.md) template** you can directly use for both tasks. I also placed **image paths exactly where your report needs them**.

---

# ARP and Default Gateway Report - 12313596

---

# Task 1: Resolving IP Addresses to Hardware Addresses (ARP)

## Aim

To understand how ARP maps IP addresses to MAC addresses in a LAN.

---

## Network Setup

* 4 × Linux Hosts (Host A, B, C, D)
* 1 × Ethernet Switch
* All hosts in same subnet (e.g. `10.10.1.0/24`)

---

## IP Addressing

| Host   | IP Address |
| ------ | ---------- |
| Host A | 10.10.1.96 |
| Host B | 10.10.1.97 |
| Host C | 10.10.1.98 |
| Host D | 10.10.1.99 |

---

## Step 1: View ARP Table (Initial State)

Run on Host A:

```bash id="arp1"
ip neigh
```

![ARP Table Initial](images/ARP-Basics-12313596-hostA-table1.png)

---

## Step 2: Ping Host B from Host A

```bash id="arp2"
ping 10.10.1.97
```

---

## Step 3: View ARP Table Again (After Ping)

```bash id="arp3"
ip neigh
```

![ARP Table After Host B](images/ARP-Basics-12313596-hostA-table2.png)

---

## Step 4: Ping Host A from Host C

On Host C:

```bash id="arp4"
ping 10.10.1.96
```

---

## Step 5: View ARP Table on Host A Again

```bash id="arp5"
ip neigh
```

![ARP Table After Host C](images/ARP-Basics-12313596-hostA-table3.png)

---

## Observations

* ARP table is updated only after communication
* MAC addresses are learned dynamically
* Entries may show state like REACHABLE or STALE

---

## Conclusion

ARP dynamically maps IP addresses to MAC addresses when communication occurs.

---

---

# Task 2: Default Gateways

## Aim

To configure default gateways and enable routing between multiple subnets.

---

## Network Topology

* 4 × Linux Hosts
* 2 × Linux Routers
* 2 × Switches
* 3 Subnets total

---

## Network Diagram

![Default Gateway Network](images/Default-Gateway-12313596-network.png)

---

## IP Addressing Scheme (Example)

### Subnet 1 (Router 1 LAN)

| Device   | IP         |
| -------- | ---------- |
| Host A   | 10.10.1.10 |
| Host B   | 10.10.1.11 |
| Router 1 | 10.10.1.1  |

---

### Subnet 2 (Router 2 LAN)

| Device   | IP         |
| -------- | ---------- |
| Host C   | 10.10.2.10 |
| Host D   | 10.10.2.11 |
| Router 2 | 10.10.2.1  |

---

### Subnet 3 (Router Interconnection)

| Device   | IP        |
| -------- | --------- |
| Router 1 | 10.10.3.1 |
| Router 2 | 10.10.3.2 |

---

## Default Gateway Configuration

On hosts (`/etc/network/interfaces`):

```bash id="gw1"
gateway 10.10.1.1
```

or

```bash id="gw2"
gateway 10.10.2.1
```

---

## Enable Routing (Routers)

```bash id="gw3"
echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward
```

---

## Disable Routing (Hosts)

```bash id="gw4"
echo 0 | sudo tee /proc/sys/net/ipv4/ip_forward
```

---

## Routing Tables

Run on all devices:

```bash id="gw5"
ip route
```

---

## Connectivity Test (Ping)

From Host A to Host C:

```bash id="gw6"
ping 10.10.2.10
```

---

## Network Screenshot

![Default Gateway Network](images/Default-Gateway-12313596-network.JPEG)

---

## Ping Success Screenshot

![Ping Result](images/Default-Gateway-12313596-ping.png)

---

## Outputs Checklist

* Project file: `Default-Gateway-12313596.gns3project`
* Network diagram: `Default-Gateway-12313596-network.png`
* ARP table screenshots
* Routing tables
* Successful ping screenshot

---

## Conclusion

* ARP resolves IP → MAC within LAN
* Default gateway enables communication across subnets
* Routers forward traffic between networks

---

If you want, I can next:
✔ correct your exact IP plan for this topology
✔ or draw a clean diagram layout for GNS3 (so your screenshot looks perfect for marks)
✔ or help you understand default gateway vs OSPF difference (exam question favourite)
