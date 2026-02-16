# Arista EVPN MLAG Firewall L2 Multicast

## Overview

This repository contains configuration examples and deployment
references for an Arista-based EVPN/VXLAN fabric integrating:

-   EVPN 
-   VXLAN overlays
-   MLAG (Multi-Chassis Link Aggregation)
-   Layer 2 extensions
-   Multicast support
-   Firewall integration within the fabric

The configurations are intended for lab, validation, and reference
purposes. They demonstrate how to build a scalable and resilient data
center fabric using Arista EOS.

This example can be used to place EVPN on top of your existing OSPF 
infrastructure for firewall consolidation.

------------------------------------------------------------------------

## Topology Features

-   Spine--Leaf architecture
-   OSPF underlay
-   BGP EVPN control plane
-   VXLAN data plane
-   MLAG leaf pair configuration
-   Layer 2 VLAN extension across the fabric
-   Multicast-enabled transport
-   Firewall connectivity at Layer 2

------------------------------------------------------------------------

## Technologies Used

-   Arista EOS
-   BGP EVPN
-   OSPF
-   VXLAN
-   MLAG
-   PIM (Protocol Independent Multicast)
-   VLAN / SVIs
-   Layer 2 trunking
-   eBGP / iBGP

------------------------------------------------------------------------

## Repository Structure

Typical configuration sections may include:

-   Spine configurations
-   Leaf configurations
-   MLAG peer configurations
-   Underlay OSPF setup
-   Overlay EBGP/EVPN setup
-   VLAN and VNI mappings
-   Multicast configuration
-   Firewall connectivity configuration

------------------------------------------------------------------------

## Deployment Notes

1.  Configure the underlay routing (typically eBGP between spine and
    leaf).

2.  Establish loopback interfaces for VTEP and BGP peering.

3.  Configure VXLAN and map VLANs to VNIs.

4.  Enable BGP EVPN address-family.

5.  Configure MLAG between leaf pairs.

6.  Enable multicast (if required) in the underlay.

7.  Validate MAC/IP route propagation using:

    ``` bash
    show bgp evpn summary
    show vxlan vni
    show interfaces vxlan
    show bgp evpn route-type mac-ip detail
    show bgp evpn route-type imet detail
    show bgp evpn route-type spmsi detail
    show multicast ipv4 evpn decap received
    ```

------------------------------------------------------------------------

## Validation Commands

Useful verification commands:

``` bash
show bgp evpn summary
show vxlan vni
show interfaces vxlan
show mlag detail
show multicast ipv4 evpn decap received
show l2rib input bgp
show ip pim interfaces
show ip pim neighbor
show ip pim upstream joins
show ip mroute detail
```

------------------------------------------------------------------------

## Requirements

-   Arista EOS compatible platform (vEOS, 7050/7280/7500 series, etc.)
-   Basic familiarity with BGP and EVPN
-   Lab environment or production-grade hardware
-   Multicast-enabled underlay (if using multicast replication)

------------------------------------------------------------------------

## Disclaimer

These configurations are provided as examples for educational and lab
use. Review and validate all configurations before deploying in a
production environment.

------------------------------------------------------------------------

## License

This project is provided for reference and learning purposes.
