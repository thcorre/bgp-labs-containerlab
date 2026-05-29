# BGP Labs for Nokia SR OS

## Chapter Labs Overview

### Chapter 3: MPLS/BGP IP-VPNs
**Lab 1: 01-basic-ipvpn**
- MPLS/BGP IP-VPN (RFC 4364)
- VRF with Route Targets and Route Distinguishers
- VPNv4 address family
- PE-CE BGP routing

**Lab 2: 02-as-path-encoding**
- AS Path Encoding (Global ASN, VRF ASN, Local-AS, no-prepend-global-as)

**Lab 3: 03-route-target-constraint**
- Route Target Constraint (RFC 4684)
- Automatic Route Filtering
- Reduced VPNv4 table size on PEs
- RTC advertisement to Route Reflectors

**Lab 4: 04-ospf-pe-ce**
- OSPF as PE-CE protocol with Sham-Links

**Lab 5: 05-inter-as-ipvpn**
- Inter-AS Type B interconnect (EBGP VPN-IPv4 between ASBRs)
- Next-Hop-Self on ASBRs
- VPN label swapping at ASBRs
- vpn-apply-import/export policies

---

## Usage Instructions

### Deploying a Lab

```bash
# Deploy the lab
sudo containerlab deploy -t 01-basic-ipvpn.clab.yml

# View deployed nodes
sudo containerlab inspect -t 01-basic-ipvpn.clab.yml
```

### Connecting to Nodes

```bash
# SSH to a node (default: admin/NokiaSros1!)
ssh admin@clab-ch03-01-basic-ipvpn-R1

# Or use docker exec
docker exec -it clab-ch03-01-basic-ipvpn-R1 sr_cli
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
sudo containerlab destroy -t 01-basic-ipvpn.clab.yml
```

---

## References

- [Versatile Routing and Services with BGP - Volume II](http://tiny.cc/Nokia-BGP-book-vol2)
- [Containerlab Documentation](https://containerlab.dev)
- [Nokia SR OS Documentation](https://documentation.nokia.com/sr/)