# CCNA Switching Lab - VLAN, VTP, Inter-VLAN Routing, STP & Layer 2 Security

## Overview

This repository contains a comprehensive Cisco Packet Tracer lab implementing core CCNA Switching concepts. The project focuses on network segmentation, VLAN management, inter-VLAN communication, spanning tree operation, and Layer 2 security mechanisms.

## Technologies and Concepts Covered

### VLAN (Virtual Local Area Network)

* VLAN 10 – HR Department
* VLAN 20 – Sales Department
* VLAN 30 – IT Department
* VLAN 99 – Management VLAN

### Trunking

* IEEE 802.1Q trunk configuration
* Native VLAN configuration (VLAN 99)
* Trunk links between switches and router

### VTP (VLAN Trunking Protocol)

* VTP Server configuration
* VTP Client configuration
* VLAN propagation across switches
* VTP domain management

### Inter-VLAN Routing

* Router-on-a-Stick implementation
* Subinterface configuration
* Communication between different VLANs

### Spanning Tree Protocol (STP)

* Root Bridge election
* STP verification
* Root Primary configuration
* Loop prevention concepts

### Layer 2 Security

* Port Security
* Sticky MAC Address learning
* Violation mode configuration
* Access port security implementation

---

## Network Topology

```
             Router 2901
                  |
               Trunk
                  |
           SW0 (VTP Server)
           /      |      \
          /       |       \
         /        |        \
  SW1(Client) SW2(Client) SW3(Client)
```

---

## Router-on-a-Stick Configuration

Configured subinterfaces:

* G0/0.10 → 192.168.10.1/24
* G0/0.20 → 192.168.20.1/24
* G0/0.30 → 192.168.30.1/24
* G0/0.99 → 192.168.99.1/24

Enabled communication between all VLANs.

---

## STP Configuration

Configured SW0 as Root Bridge:

spanning-tree vlan 10,20,30,99 root primary

Purpose:

* Control STP topology
* Ensure central switch becomes Root Bridge
* Prevent Layer 2 loops

---

## Port Security Configuration

Configured on user access ports:

switchport port-security
switchport port-security maximum 1
switchport port-security mac-address sticky
switchport port-security violation shutdown

Features:

* Learns MAC address automatically
* Restricts unauthorized devices
* Protects switch access ports

---

## Troubleshooting Performed

### Native VLAN Mismatch

Issue:

CDP native VLAN mismatch errors appeared between switches.

Cause:

* One side configured with Native VLAN 99
* Other side configured with Native VLAN 1

Resolution:

* Standardized Native VLAN 99 on all trunk links

---

### Trunk vs Access Port Misconfiguration

Issue:

* Switch ports configured as access instead of trunk
* VLAN traffic failed across switches

Resolution:

* Converted inter-switch links to trunk ports
* Verified using:

show interfaces trunk

---

### Inter-VLAN Routing Failure

Issue:

* VLAN 30 and VLAN 99 hosts could not communicate

Cause:

* Trunk inconsistencies and native VLAN mismatch

Resolution:

* Corrected trunk configuration
* Verified router subinterfaces
* Tested end-to-end connectivity

---

### VTP Verification

Issue:

* Needed confirmation that VLANs propagated correctly

Verification:

show vtp status
show vlan brief

Result:

* VLANs successfully synchronized across clients

---

### Port Security Configuration Issue

Issue:

* Sticky MAC configured but Port Security not enabled

Incorrect:

switchport port-security mac-address sticky

Correct:

switchport port-security
switchport port-security mac-address sticky

Resolution:

* Enabled Port Security properly
* Verified with:

show port-security interface fa0/1

---

## Verification Commands

### VLAN

show vlan brief

### Trunk

show interfaces trunk

### VTP

show vtp status

### STP

show spanning-tree

### Router

show ip interface brief

### Port Security

show port-security
show port-security interface fa0/1
show port-security address

---

## Skills Gained

* VLAN Configuration
* Trunking Configuration
* VTP Management
* Router-on-a-Stick
* Inter-VLAN Routing
* STP Root Bridge Election
* Layer 2 Troubleshooting
* Port Security
* Network Verification Commands
* Cisco Packet Tracer Lab Design

---

## Author

Gokulakannan V

B.Tech Computer Science and Engineering

Vel Tech Rangarajan Dr. Sagunthala R&D Institute of Science and Technology
