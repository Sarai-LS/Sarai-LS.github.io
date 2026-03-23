---
title: "Secure Enterprise Network Design - Segmentation, Routing, and Firewall Enforcement in Cisco Packet Tracer"
date: 2026-03-21
categories: [portfolio, network-security, infrastructure]
tags:
  - network-security
  - cisco
  - packet-tracer
  - vlan
  - firewall
  - segmentation
  - acl
---

## **Overview**
This project demonstrates the design and implementation of a secure enterprise network architecture using Cisco Packet Tracer. Ths goal was to simulate a realistic organizational environment with multuple departments, enforce network segmentation, and apply security controls to reduce unauthorized access and lateral movement.

The network was designed with a layered approach, incorporating VLAN segmentation, inter-VLAN routing, and access control lists (ACLs) to establish and enforce trust boundaries between internal systems.

## **Project Summary**
- **Objective:** Design a segmented and secure enterprise network
- **Core Components:** VLANs, Router-on-a-Stick, ACLs
- **Security Focus:** Least privilege, network segmentation, controlled access
- **Key Outcome:** Verified enforcement of restricted communication between network zones

## **Architecture Overview**
The network topology was structured as follows:

![Full Topology](/assets/full_topology.png)
_Note: A firewall (Cisco ASA) was initially introduced between the router and switch to simulate perimiter security. However, due to VLAN trunking limitations within Packet Tracer, the final implementation enforces security controls at the routing layer using ACLs._


## **VLAN Segmentation:**
- **VLAN 10 -** Users
- **VLAN 20 -** IT/Admin
- **VLAN 30 -** Internal Servers
- **VLAN 40 -** DMZ (Public-facing services)

This segmentation establishes distinct trust zones and reduces the risk of lateral movement across the network.

![VLAN Config](/assets/vlan_switch.png)

## **Inter-VLAN Routing (Router-on-a-Stick)**
A router-on-a-stick configuration was implemented using subinterfaces for each VLAN. Each subinterface acts as the default gateway for its respective network.

This design:
- Centralizes routing decisions
- Creates a control point for traffic inspection
- Reflects common small-to-mid scale enterprise architecture

![Router Subinterfaces](/assets/router_subinterfaces.png)

## **Access Control Lists (ACLs)**
ACLs were implemented to enforce **least privilege access control** between VLANs.

**Key Policies:**
- Users **cannot access** Server VLAN
- Users **cannot access** IT VLAN
- IT/Admin access can be extended for management (optional)
- All other traffic is permitted as needed

Example ACL:

![ACL Configuration](/assets/acl_configuration.png)

## **Security Validation (Testing)**
The network was tested to validate both **Allowed and restricted communication paths.**

**Allowed:**
- User --> Default Gateway (```192.168.10.1```)

_Output:_
![Successful Ping](/assets/successful_ping_pc.png)

**Blocked:**
- User --> Server VLAN (```192.168.30.10```)

_Output:_
![Failed Ping](/assets/failed_ping_pc.png)

These results confirm that traffic is being evaluated and denied according to defined security policies.

## **Secuity Controls Implemented**
- VLAN-based segmentation
- Centralized inter-VLAN routing
- ACL-based policy enforcement
- Logical separation of trust zones

These controls reduce:
- Unauthorized access
- Lateral movement
- Exposure of critical systems

## **Threat Considerations**
This design accounts for:
- **Lateral Movement:** Mitigated through segmentation and ACL enforcement
- **Unauthorized Access:** Controlled via least privilge policies
- **Overexposed Services:** DMZ concept isolates public-facing systems
- **Misconfigured Acces:** Explicit rule-based filtering reduces risk

## **Real-World Relevance**
This project reflects real-world cybersecurity engineering concepts:
- Network segmentation by role
- Policy-based traffic control
- Secure infrastructure design
- Enforcement of least privilege

While implemented in a simulated environment, the architectural decisions align with enterprise security practices.

## **Challenges & Lessons Learned**
One of the main challenges encountered was integrating a firewall (Cisco ASA) into a VLAN-based architecture within Packet Tracer.

This highlighted:
- The importance of hacing a correct Layer 2 vs Layer 3 design
- How security devices can impact traffic flow
- The complexity of placing controls without breaking functionality

As a result, security enforcement was shifted to the routing layer using ACLs, ensuring both functionality and policy enforcement.

## **Conclusion**
This project demonstrates my ability to design and implement a secure network architecture with a focus on segmentation, access control, and security design. 

It reflects my approach to cybersecurity engineering by:
- Thinking in terms of risk reduction
- Enforcing least privilege
- Designing systems with clear trust boundaries

## **Download the Cisco Packet Tracer Project**
You can download the full Cisco Packet Tracer file to explore the network yourself!

[Download Packet Tracer Project](/assets/sarai_cyber_engineering_project.pkt)