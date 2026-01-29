# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

BGP network labs using Containerlab with Nokia SR-OS (SR-SIM) routers. Labs are companion materials for "Versatile Routing and Services with BGP - Volume II" by Colin Bookham, organized by book chapters (ch02-ch13).

## Common Commands

```bash
# Deploy a lab
sudo containerlab deploy -t <path-to-topology.clab.yml>

# Destroy a lab
sudo containerlab destroy -t <path-to-topology.clab.yml>

# Inspect running lab
sudo containerlab inspect -t <path-to-topology.clab.yml>

# Connect to a node (default credentials: admin/admin)
ssh admin@clab-<lab-name>-<node-name>
# Or via docker
docker exec -it clab-<lab-name>-<node-name> sr_cli
```

## Repository Structure

Each chapter directory contains:
- `*.clab.yml` - Containerlab topology file defining nodes and links
- `configs/` - Nokia SR-OS startup configurations in MD-CLI format (`.cfg` files)

## File Formats

### Topology Files (`.clab.yml`)
- YAML format defining `topology.kinds`, `topology.nodes`, and `topology.links`
- Nodes reference kind `nokia_srsim` with image, type, and license path
- Startup configs point to files in `configs/` subdirectory

### Configuration Files (`.cfg`)
- Nokia SR-OS MD-CLI format (YANG-based, hierarchical with curly braces)
- Key sections: `system`, `card`, `port`, `router "Base"` (interfaces, OSPF, BGP), `service` (VPN services)
- Configurations applied atomically via `commit`

## SR-OS Show Commands Reference

```
show router bgp summary          # BGP session overview
show router bgp neighbor         # Neighbor details
show router bgp routes           # IPv4 unicast routes
show router bgp routes vpn-ipv4  # L3VPN routes
show router bgp routes evpn      # EVPN routes
show router interface            # Interface status
show router ospf neighbor        # OSPF adjacencies
show router ldp bindings active  # LDP label bindings
show router mpls-labels summary  # MPLS label table
show service id <id> base        # VPN service status
```

## Prerequisites

- Linux host with Docker (20.10+) and Containerlab (0.72.0+)
- Nokia SR-SIM container image (nokia_srsim:25.10.R1)
- SR-OS license file at `/opt/nokia/sros/license.txt`
