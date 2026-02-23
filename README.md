# Enterprise-Network-OSPF-ACL
Enterprise network simulation using OSPF with extended ACL-based access control and validation tests

# Enterprise Network Design with OSPF & ACL Security

## Overview
This project simulates a small enterprise network with three departments: HR, Finance, and IT. The network is designed to demonstrate:

- VLAN-based departmental segmentation
- Dynamic routing using OSPF (Area 0 backbone)
- Extended ACL implementation to enforce inter-department access control
- Fault testing and connectivity validation

The goal is to show practical network design, routing configuration, and security enforcement in a controlled environment.

---

## Network Architecture
- **Departments:** HR (192.168.10.0/24), Finance (192.168.20.0/24), IT (192.168.30.0/24)  
- **Routers:** 3 routers connected via serial links (/30 subnets)  
- **Switches:** 3, one per department  
- **PCs:** 2 per department  
- **Routing:** OSPF, Area 0 backbone

Design Notes:
- HR → Finance traffic is blocked using an extended ACL applied on the HR-facing router interface.  
- All other inter-department traffic is allowed.

---

## Routing Protocol
- **Protocol Used:** OSPF (Open Shortest Path First)  
- **Process ID:** 1  
- **Why OSPF:**  
  - Supports hierarchical network design with areas  
  - Fast convergence  
  - Widely used in enterprise environments  
- All networks are advertised within Area 0 for proper route propagation.

---

## Security Policy (ACL)
- **ACL Name/Number:** 101  
- **Purpose:** Block HR department from accessing Finance while allowing all other communication.  
- **Implementation:** Applied inbound on HR router interface connecting to HR switch.  

**ACL Rules:**
1. Deny HR → Finance  
2. Permit all other traffic  

- Confirmed using Packet Tracer ping tests and `show access-lists`.

---

## Testing & Validation
- Verified OSPF adjacency between all routers.  
- Confirmed dynamic route learning via `show ip route`.  
- Tested ACL enforcement:
  - HR → Finance ping → **blocked**  
  - HR → IT ping → **successful**  
- Ensured all interfaces were configured with correct IP addressing and `no shutdown`.

---

## Files in This Repository
- `Enterprise-Network.pkt` → Packet Tracer file of the network  
- `/images` → Screenshots of topology, routing table, ACL configuration, and ping results  

---

## Notes
This project demonstrates both technical skill and understanding of enterprise networking principles, including:

- Practical OSPF configuration  
- Security policy enforcement with ACLs  
- Validation and troubleshooting methods  
- Clear documentation for professional presentation
