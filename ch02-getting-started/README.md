# BGP Labs for Nokia SR OS

## Chapter Labs Overview

### Chapter 2: Getting Started
**Lab: basic-bgp-session**
- Basic EBGP and IBGP session configuration
- Session negotiation and capabilities
- BGP Finite State Machine (FSM)
- Multi-Protocol BGP (MP-BGP)

---

## Usage Instructions

### Deploying a Lab

```bash
# Deploy the lab
sudo containerlab deploy -t basic-bgp-session.clab.yml

# View deployed nodes
sudo containerlab inspect -t basic-bgp-session.clab.yml
```

### Connecting to Nodes

```bash
# SSH to a node (default: admin/NokiaSros1!)
ssh admin@clab-ch02-basic-bgp-session-R1

# Or use docker exec
docker exec -it clab-ch02-basic-bgp-session-R1 sr_cli
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
show service id 1 base

# MPLS labels
show router mpls-labels summary
```

### Destroying a Lab

```bash
sudo containerlab destroy -t basic-bgp-session.clab.yml
```

---

## References

- [Versatile Routing and Services with BGP - Volume II](http://tiny.cc/Nokia-BGP-book-vol2)
- [Containerlab Documentation](https://containerlab.dev)
- [Nokia SR OS Documentation](https://documentation.nokia.com/sr/)