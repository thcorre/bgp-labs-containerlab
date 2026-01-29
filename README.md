# BGP Labs for Nokia SR-OS (Containerlab)

## Overview

This repository contains containerlab topology files and Nokia SR-OS configurations for hands-on labs based on **"Versatile Routing and Services with BGP - Volume II"** by Colin Bookham.

Each lab is designed to demonstrate specific BGP features and technologies covered in the book, allowing readers to gain practical experience with the concepts.

## Prerequisites

### Software Requirements
- Linux host (Ubuntu 20.04+ recommended)
- Docker (20.10+)
- Containerlab (0.72.0+)
- Nokia SR-SIM container image (or vr-sros with vrnetlab)

### Installation

```bash
# Install Containerlab
bash -c "$(curl -sL https://get.containerlab.dev)"

# Verify installation
containerlab version
```

### Nokia SR-SIM Image

You'll need to obtain the Nokia SR-SIM image from Nokia. Once obtained:

```bash
# Import the image (adjust path as needed)
docker load -i nokia_srsim-25.10.R1.tar.gz

# Verify
docker images | grep nokia_srsim
```

### License File

Place your SR-OS license file at `/opt/nokia/sros/license.txt` or update the topology files to point to your license location.

---

## Lab Directory Structure

```
bgp-labs/
├── README.md                          # This file
├── ch02-getting-started/              # Chapter 2: Getting Started
│   ├── basic-bgp-session.clab.yml
│   └── configs/
├── ch03-mpls-bgp-ipvpn/               # Chapter 3: MPLS/BGP IP-VPNs
│   ├── 01-basic-l3vpn.clab.yml
│   ├── 02-inter-as-option-c.clab.yml
│   ├── 03-route-target-constraint.clab.yml
│   └── configs/
├── ch04-bgp-vpls/                     # Chapter 4: Using BGP in VPLS
│   ├── bgp-vpls-autodiscovery.clab.yml
│   └── configs/
├── ch05-bgp-vpws/                     # Chapter 5: BGP Signalling for VPWS
│   ├── bgp-vpws.clab.yml
│   └── configs/
├── ch06-evpn/                         # Chapter 6: Ethernet VPN
│   ├── 01-evpn-vpls.clab.yml
│   ├── 02-evpn-rt5-ipprefix.clab.yml
│   └── configs/
├── ch07-labeled-unicast/              # Chapter 7: Labeled Unicast IPv4
│   ├── seamless-mpls-inter-as.clab.yml
│   └── configs/
├── ch08-segment-routing/              # Chapter 8: Segment Routing and BGP
│   ├── sr-bgp-prefix-sid.clab.yml
│   └── configs/
├── ch09-reconvergence/                # Chapter 9: Reconvergence
│   ├── addpath-pic.clab.yml
│   └── configs/
├── ch10-multicast/                    # Chapter 10: Multicast
│   ├── mvpn.clab.yml
│   └── configs/
├── ch11-graceful-restart/             # Chapter 11: Graceful Restart
│   ├── graceful-restart.clab.yml
│   └── configs/
├── ch12-security/                     # Chapter 12: Security
│   ├── flowspec-rtbh.clab.yml
│   └── configs/
└── ch13-general-topics/               # Chapter 13: General Topics
    ├── multipath-bgpls-orr.clab.yml
    └── configs/
```

---

## Chapter Labs Overview

### Chapter 2: Getting Started
**Lab: basic-bgp-session**
- Basic EBGP and IBGP session configuration
- Session negotiation and capabilities
- BGP Finite State Machine (FSM)
- Multi-Protocol BGP (MP-BGP)

### Chapter 3: MPLS/BGP IP-VPNs
**Lab 1: 01-basic-l3vpn**
- MPLS/BGP IP-VPN (RFC 4364)
- VRF with Route Targets and Route Distinguishers
- VPNv4 address family
- PE-CE routing (static and BGP)

**Lab 2: 02-inter-as-option-c**
- Inter-AS Option C (RFC 4364 Section 10c)
- EBGP labeled unicast between ASBRs
- VPNv4 route exchange via Inter-AS Route Reflectors
- Multi-hop EBGP for VPNv4

**Lab 3: 03-route-target-constraint**
- Route Target Constraint (RFC 4684)
- Automatic Route Filtering
- Reduced VPNv4 table size on PEs
- RTC advertisement to Route Reflectors

### Chapter 4: Using BGP in VPLS
**Lab: bgp-vpls-autodiscovery**
- BGP Auto-Discovery with LDP Signalling
- BGP Auto-Discovery and Signalling (RFC 4761)
- VPLS Multi-Homing

### Chapter 5: BGP Signalling for VPWS
**Lab: bgp-vpws**
- Single-homed VPWS with BGP signalling
- Multi-homed VPWS (Active/Standby)
- Pseudowire redundancy

### Chapter 6: Ethernet VPN
**Lab 1: 01-evpn-vpls**
- EVPN Route Types (1-5)
- EVPN-VPLS service
- Ethernet Segments for multi-homing
- Active/Active multi-homing
- MAC Advertisement and BUM handling

**Lab 2: 02-evpn-rt5-ipprefix**
- EVPN Route-Type 5 (IP Prefix Advertisement)
- Interface-ful with SBD IRB model
- Interface-less IP-VRF-to-IP-VRF model
- EVPN-VXLAN overlay in Data Center fabric

### Chapter 7: Labeled Unicast IPv4
**Lab: seamless-mpls-inter-as**
- Seamless MPLS with BGP labeled unicast
- Multi-area MPLS transport
- Inter-AS Option C
- BGP-LDP FEC stitching

### Chapter 8: Segment Routing and BGP
**Lab: sr-bgp-prefix-sid**
- BGP Prefix-SID distribution
- SR-MPLS with BGP labeled unicast
- IS-IS Segment Routing integration
- SR transport for VPN services

### Chapter 9: Reconvergence
**Lab: addpath-pic**
- ADD-PATH (multiple path advertisement)
- Prefix Independent Convergence (PIC)
- Best External
- Next-Hop Tracking
- Minimum Route Advertisement Interval (MRAI)

### Chapter 10: Multicast
**Lab: mvpn**
- Multicast VPN (MVPN) with BGP signalling
- MVPN Route Types
- P-tunnels (mLDP)

### Chapter 11: Graceful Restart and Error Handling
**Lab: graceful-restart**
- BGP Graceful Restart mechanism
- GR Helper mode
- Long-Lived Graceful Restart (LLGR)
- Error handling

### Chapter 12: Security
**Lab: flowspec-rtbh**
- FlowSpec for DDoS mitigation
- Remote Triggered Black-Holing (RTBH)
- Generalized TTL Security Mechanism (GTSM)
- TCP-AO authentication

### Chapter 13: General Topics
**Lab: multipath-bgpls-orr**
- IBGP/EBGP Multipath (ECMP)
- BGP-LS (Link State Distribution)
- Optimal Route Reflection (ORR)
- BGP Monitoring Protocol (BMP)

---

## Usage Instructions

### Deploying a Lab

```bash
# Navigate to the lab directory
cd bgp-labs/ch03-mpls-bgp-ipvpn

# Deploy the lab
sudo containerlab deploy -t basic-l3vpn.clab.yml

# View deployed nodes
sudo containerlab inspect -t basic-l3vpn.clab.yml
```

### Connecting to Nodes

```bash
# SSH to a node (default: admin/admin)
ssh admin@clab-ch03-mpls-bgp-ipvpn-PE1

# Or use docker exec
docker exec -it clab-ch03-mpls-bgp-ipvpn-PE1 sr_cli
```

### Useful Show Commands

```bash
# BGP summary
show router bgp summary

# BGP neighbors
show router bgp neighbor

# BGP routes
show router bgp routes

# VPNv4 routes
show router bgp routes vpn-ipv4

# EVPN routes
show router bgp routes evpn

# Service status
show service id 100 base

# MPLS labels
show router mpls-labels summary
```

### Destroying a Lab

```bash
sudo containerlab destroy -t basic-l3vpn.clab.yml
```

---

## Configuration Notes

### SR-OS MD-CLI Format
All configurations use the SR-OS MD-CLI (Model-Driven CLI) format introduced in SR-OS 19.x. Key characteristics:
- Hierarchical structure using curly braces `{}`
- Configuration is applied atomically via `commit`
- Uses YANG-based data models

### Common Configuration Patterns

**BGP Neighbor Configuration:**
```
router "Base" {
    bgp {
        admin-state enable
        group "IBGP" {
            peer-as 64496
            local-address 192.0.2.1
            family {
                ipv4 true
                vpn-ipv4 true
            }
        }
        neighbor "192.0.2.2" {
            group "IBGP"
        }
    }
}
```

**VPRN (L3VPN) Configuration:**
```
service {
    vprn "VPN-A" {
        admin-state enable
        service-id 100
        customer "1"
        route-distinguisher "64496:100"
        vrf-target {
            community "target:64496:100"
        }
        interface "to-CE" {
            sap 1/1/2 {
            }
        }
    }
}
```

---

## Troubleshooting

### Common Issues

1. **License not found**
   - Verify license file path in topology YAML
   - Ensure license is valid for the SR-OS version

2. **Nodes not coming up**
   - Check Docker resources (CPU/memory)
   - Wait 1-2 minutes for SR-SIM to boot fully
   - Use `docker logs <container>` to check boot status

3. **BGP sessions not establishing**
   - Verify IGP/OSPF adjacencies
   - Check interface configurations
   - Ensure system interfaces (loopbacks) are reachable

### Debug Commands

```bash
# Enable BGP debug
debug router bgp neighbor <ip>

# Check logs
show log log-id 99

# Interface status
show router interface

# OSPF neighbors
show router ospf neighbor

# LDP bindings
show router ldp bindings active
```

---

## References

- [Versatile Routing and Services with BGP - Volume II](http://tiny.cc/Nokia-BGP-book-vol2)
- [Containerlab Documentation](https://containerlab.dev)
- [Nokia SR OS Documentation](https://documentation.nokia.com/sr/)
- [Nokia Network Developer Portal](https://network.developer.nokia.com)

---

## Contributing

Feel free to submit issues or pull requests to improve the labs or add new scenarios.

## License

These lab materials are provided for educational purposes. Nokia SR-OS requires appropriate licensing from Nokia.
