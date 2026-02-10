# BGP Labs for Nokia SR OS (Containerlab)

## Overview

This repository contains containerlab topology files and Nokia SR OS configurations for hands-on labs based on Colin Bookham's **"[Versatile Routing and Services with BGP - Volume II](http://tiny.cc/Nokia-BGP-book-vol2)"**.

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
docker load -i nokia_srsim-25.10.R2.tar.gz

# Verify
docker images | grep nokia_srsim
```

### License File

Place your SR OS license file at `/opt/nokia/sros/license.txt` or update the topology files to point to your license location.

---

## Lab Directory Structure

```
bgp-labs/
├── README.md                                 # This file
├── ch02-getting-started/                     # Chapter 2: Getting Started
│   ├── basic-bgp-session.clab.yml
│   └── configs/
├── ch03-mpls-bgp-ipvpn/                      # Chapter 3: MPLS/BGP IP-VPNs
│   ├── 01-basic-l3vpn.clab.yml                 # Basic L3VPN with R1-R6, RR1, CE1/CE3/CE4/CE6
│   ├── 02-inter-as-option-b.clab.yml           # Inter-AS Type B with R1, ASBR1, ASBR2, R6, RR1, RR2
│   ├── 03-route-target-constraint.clab.yml     # RTC lab with R1, R3, R4, R6, RR1
│   └── configs/
├── ch04-bgp-vpls/                            # Chapter 4: Using BGP in VPLS
│   ├── bgp-vpls-autodiscovery.clab.yml
│   └── configs/
├── ch05-bgp-vpws/                            # Chapter 5: BGP Signalling for VPWS
│   ├── bgp-vpws.clab.yml
│   └── configs/
├── ch06-evpn/                                # Chapter 6: Ethernet VPN
│   ├── 01-evpn-vpls.clab.yml
│   ├── 02-evpn-rt5-ipprefix.clab.yml
│   └── configs/
├── ch07-labeled-unicast/                     # Chapter 7: Labeled Unicast IPv4
│   ├── seamless-mpls-inter-as.clab.yml
│   └── configs/
├── ch08-segment-routing/                     # Chapter 8: Segment Routing and BGP
│   ├── sr-bgp-prefix-sid.clab.yml
│   └── configs/
├── ch09-reconvergence/                       # Chapter 9: Reconvergence
│   ├── addpath-pic.clab.yml
│   └── configs/
├── ch10-multicast/                           # Chapter 10: Multicast
│   ├── mvpn.clab.yml
│   └── configs/
├── ch11-graceful-restart/                    # Chapter 11: Graceful Restart
│   ├── graceful-restart.clab.yml
│   └── configs/
├── ch12-security/                            # Chapter 12: Security
│   ├── flowspec-rtbh.clab.yml
│   └── configs/
└── ch13-general-topics/                      # Chapter 13: General Topics
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

**Lab 2: 02-inter-as-option-b**
- Inter-AS Option B
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

### SR OS MD-CLI Format
All configurations use the SR OS MD-CLI (Model-Driven CLI) format introduced in release 16. Key characteristics:
- Hierarchical structure using curly braces `{}`
- Configuration is applied atomically via `commit`
- Uses YANG-based data models

### Common Configuration Patterns

**BGP Neighbor Configuration:**
```
configure router "Base" {
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
configure service {
    vprn "VPN-A" {
        admin-state enable
        service-id 100
        customer "1"
        bgp-ipvpn {
            mpls {
                admin-state enable
                route-distinguisher "64496:100"
                vrf-target {
                    community "target:64496:100"
                }
            }
        }
        interface "to-CE" {
            ipv4 {
                primary {
                    address 192.0.2.1
                    prefix-length 30
                }
            }
            sap 1/1/c2/1 {
            }
        }
    }
}
```

---

## Packet capture

Every network labbing software must provide its users with the packet capturing abilities. Looking at the frames as they traverse the network links is not only educational, but also helps to troubleshoot the issues that might arise during the lab development. Also, this collection of BGP labs requires to have a deeper understanding of the packet exchanges between peers as well the different fieds and values within those packets.

Containerlab offers a simple way to capture the packets from any interface of any node in the lab since every interface is exposed to the underlying Linux OS. This article will explain how to do that.

Everything we are going to do in this exercise is explained in details in the [Containerlab documentation](https://containerlab.dev/manual/wireshark/).

### Remote capture

The first way to capture the packets from a containerlab node running on a remote host that we are going to explore is called "remote capture". In this scenario a user has a network connectivity (ssh) to the host that runs containerlab topology and wishes to get the packet capture displayed in the Wireshark running locally.

To achieve this, we will execute the `tcpdump` command on the remote host and pipe the output to the local Wireshark app. Here is a command that does it all for the host `d1` which is the instructors host.

It captures the traffic from SR OS (`clab-vm-sros`) port `eth1` (`1/1/1`) running on `d1` host and displaying the capture in the Wireshark.

<small>The command is provided for WSL and Mac systems, assuming default Wireshark installation path</small>

Windows/WSL:

```bash
ssh root@{public_IP} \
"ip netns exec clab-vm-sros tcpdump -U -nni eth1 -w -" | \
/mnt/c/Program\ Files/Wireshark/wireshark.exe -k -i -
```

macOS:

```
ssh root@{public_IP} \
"ip netns exec clab-vm-sros tcpdump -U -nni eth1 -w -" | \
/Applications/Wireshark.app/Contents/MacOS/Wireshark  -k -i -
```

### Visual Studio Code

`tcpdump` is great, but what we really want to see is that Wireshark window we know and love.

Thanks to the VS Code extension, you can capture as many packets as you wish without even changing applications.

Open the extension pane and expand the tree view on the left hand side to drill down to the interface level.

Upon hovering on an interface, you should see shark icon. Click the shark icon and watch as the magic happens and wireshark opens right inside of VS Code.

![](https://gitlab.com/rdodin/pics/-/wikis/uploads/752c161fe4e66750a35e0031e7e7d2f7/vscode_wireshark_vnc.gif)

Under the hood this relies on the Edgeshark integration, which is discussed next.

### Edgeshark

[Edgeshark](https://edgeshark.siemens.io/#/) is a set of tools that offer (among many things) a Web UI that displays every interface of every container and can start a wireshark as easy as clicking a button.

Edgeshark installation consists of two parts:

1. A service that runs on the host that runs containerlab topologies
2. A wireshark capture plugin that runs next to the Wireshark on a user's PC

To install the service, past the installer command that uses docker compose to deploy the service:

```bash
curl -sL \
https://github.com/siemens/edgeshark/raw/main/deployments/wget/docker-compose.yaml | \
docker compose -f - up -d
```

Now, you have to install the client plugin based on the OS of your PC.

#### Windows:

Windows users get to enjoy a simple installer-based workflow that installs the URL handler and the Wireshark plugin in one go.

Download the [installer archive](https://github.com/siemens/cshargextcap/releases/download/v0.10.7/cshargextcap_0.10.7_windows_amd64.zip).

Unzip the archive and launch the installer.

#### MacOS:

MacOS users have to suffer a little. But it is not that bad either.

To install the URL handler paste the following in the Mac terminal app:

```bash
mkdir -p /tmp/pflix-handler && cd /tmp/pflix-handler && \
rm -rf packetflix-handler.zip packetflix-handler.app __MACOSX && \
curl -sLO https://github.com/srl-labs/containerlab/files/14278951/packetflix-handler.zip && \
unzip packetflix-handler.zip && \
sudo mv packetflix-handler.app /Applications
```

To install the extcap wireshark plugin execute in the Mac terminal:

```bash
# for x86_64 MacOS use https://github.com/siemens/cshargextcap/releases/download/v0.10.7/cshargextcap_0.10.7_darwin_amd64.tar.gz
DOWNLOAD_URL=https://github.com/siemens/cshargextcap/releases/download/v0.10.7/cshargextcap_0.10.7_darwin_arm64.tar.gz
mkdir -p /tmp/pflix-handler && curl -sL $DOWNLOAD_URL | tar -xz -C /tmp/pflix-handler && \
open /tmp/pflix-handler && open /Applications/Wireshark.app/Contents/MacOS/extcap
```

The command above will open two Finder windows, one with the `cshargextcap` binary and the other with the Wireshark's existing plugins. Move the `cshargextcap` file over to the window with Wireshark plugins.

#### Web UI

To access the Edgeshark UI, open a browser and navigate to the following URL:

[http://localhost:5001](http://localhost:5001)

Note, the http schema is important, since https is not enabled.

---

## References

- [Versatile Routing and Services with BGP - Volume II](http://tiny.cc/Nokia-BGP-book-vol2)
- [Containerlab Documentation](https://containerlab.dev)
- [Nokia SR OS Documentation](https://documentation.nokia.com/sr/)

---

## Contributing

Feel free to submit issues or pull requests to improve the labs or add new scenarios.

## License

These lab materials are provided for educational purposes. Nokia SR OS requires appropriate licensing from Nokia.
