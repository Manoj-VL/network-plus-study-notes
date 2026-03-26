# CompTIA Network+ Study Journey

Documenting my hands-on learning as I prepare
for the CompTIA Network+ exam using Jason Dion's
Udemy course and Cisco Packet Tracer labs.

---

## About Me
- Background: Mechanical Engineering
- Goal: Cloud Security Engineer (Microsoft Azure)
- Target: Network+ → Security+ → AZ-500

---


## Progress Tracker
| Day | Topics Covered | Lab Completed | Status |
|-----|---------------|---------------|--------|
| 1 | Network Components, Resources, Geography | Lab 1 — Basic Network | ✅ |
| 2 | Network Topologies - Wired,Wireless,Data Center | Lab 2 — Extended Network | ✅ |
| 3 | OSI Model - Physical,Data link | Lab 3 - Switch Mac Address Table | ✅ |
| 4 | OSI Model - Network,Transport,Session | 

-------

## Day 1 
### Topics Learned
- Network Components - Client,Server,Hub,Switch etc{Basics will go into detail later}
- Network Resources - Client/Server , Peer to Peer Model
- Network Geography - PAN,LAN,CAN,MAN,WAN

## Lab1 - Basic Network
**Topology**
PC1 → Switch → Router → PC2

**IP Addresses:**
- PC1 = 192.168.1.10 / gateway 192.168.1.1
- PC2 = 192.168.2.10 / gateway 192.168.2.1
- Router GigaEthernet0/0 = 192.168.1.1
- Router GigaEthernet0/1 = 192.168.2.1

**Problem I Hit:**
Red dots between router and all connected devices

**How I Fixed It:**
Router ports are OFF by default in Packet Tracer.
Had to manually turn them on using CLI:
```
enable
configure terminal
interface GigabitEthernet0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit
interface GigabitEthernet0/1
ip address 192.168.2.1 255.255.255.0
no shutdown
exit

```

**What I Learned From This:**
- Switches turn on automatically
- Routers must be manually enabled
- Routers connects two sperate networks
- no shutdown is the command to activate an interface



### Screenshot
![Lab 1 Ping]



<img width="1920" height="1080" alt="Screenshot (17)" src="https://github.com/user-attachments/assets/47b583d3-ae7e-4b43-91ee-9eba66e3a509" />

-----------

## Day 2
### Topics Learned
- Wired Topologies — Bus, Ring, Star, Mesh
- Wireless Topologies — Infrastructure, Ad Hoc, Mesh
- Data Center Topologies — Three tier, Spine and Leaf
-----

### Key Takeaways
- Star topology is most common in modern networks
  — all devices connect to central switch
- Mesh topology is most redundant but most expensive
  — every device connects to every other device
- Spine and Leaf is standard in modern data centers
  — used by companies like Microsoft Azure
----------

## Lab 2 — Extended Network
**Topology:**
PC1 → Switch → Router → Switch2 → PC2
                                └→ PC3

**IP Addresses:**
- PC1 = 192.168.1.10 / gateway 192.168.1.1
- PC2 = 192.168.2.10 / gateway 192.168.2.1
- PC3 = 192.168.2.20 / gateway 192.168.2.1

**What I Learned:**
- One router can manage multiple subnets
- Devices on same subnet communicate directly
- Devices on different subnets need router to communicate

### Screenshot


<img width="1920" height="1080" alt="Screenshot (18)" src="https://github.com/user-attachments/assets/62f6a7f6-da08-4004-8e34-d359fd43f308" />

-------

# Lab 3 — Switch MAC Address Table

**Goal:** Observe how switches learn MAC addresses at Layer 2

**Steps Taken:**
1. Pinged PC2 from PC1 to generate traffic
2. Opened Switch CLI
3. Ran "show mac-address-table" command
4. Matched PC1 MAC address to switch table entry

**Commands Used:**
enable
show mac-address-table

**What I Observed:**
- Switch automatically learned MAC addresses
  after first ping
- Each MAC address mapped to a specific port
- Type shows "DYNAMIC" meaning switch learned it
  automatically not manually configured

**What I Learned:**
- Switches build MAC table by watching traffic
- Before first ping — switch doesn't know where devices are
- After first ping — switch remembers which port each device is on
- This is called MAC address learning

### Screenshot


<img width="1920" height="1080" alt="Screenshot (20)" src="https://github.com/user-attachments/assets/7a66656d-6a33-4dc9-8778-6808d7750274" />
