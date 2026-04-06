---

copyright:
  years: 2026
lastupdated: "2026-04-06"

keywords: vpc firewall, firewall deployment, high availability, fortinet,
  palo alto, juniper, check point, f5, transit vpc, sdn connector

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}



# Firewall deployment options for VPC
{: #vpc-firewall-options}

Firewall deployment options are available for
{{site.data.keyword.vpc_full}}, including standalone, active/passive, and
active/active high availability configurations across single and multiple
availability zones.
{: shortdesc}

{{site.data.keyword.vpc_short}} is a Layer 3 Software-Defined Network (SDN)
that offers flexible firewall deployment options to meet various security and
availability requirements. Unlike IBM Cloud Classic infrastructure, which uses
a Layer 2 network architecture, VPC uses a Layer 3 SDN architecture with
multiple firewall implementation patterns.

The following sections describe the characteristics, available solutions, and
implementation options for each firewall deployment pattern.

## Firewall deployment patterns
{: #firewall-deployment-patterns}

{{site.data.keyword.vpc_short}} supports multiple firewall deployment patterns
that provide different levels of availability, scalability, and operational
complexity.

| Feature | [Standalone](#standalone-deployment) | [Active/Active HA (Single Zone)](#activeactive-ha-single-zone) | [Active/Passive HA (Single Zone)](#activepassive-ha-single-zone) | [Active/Passive HA (Multi-Zone)](#activepassive-ha-multizone) | [Active/Active HA (Multi-Zone)](#activeactive-ha-multizone) |
|---------|-------------------------------------|---------------------------------------------|----------------------------------------------|----------------------------------------------|---------------------------------------------|
| **High Availability** | None | Load balanced | Single zone failover | Regional failover | Regional load balanced |
| **Deployment Complexity** | Low | Medium | Medium | High | High |
| **Compute Options** | Virtual Server or Bare Metal | Virtual Server | Virtual Server or Bare Metal | Virtual Server | Virtual Server |
| **Failover Method** | N/A | Network Load Balancer | Virtual Server: SDN Connector /n Bare Metal: VNI Floating | SDN Connector | BGP over GRE |
| **SDN Connector Required** | No | No (uses NLB) | Virtual Server: Yes (Fortinet native) /n Bare Metal: No (uses VNI) | Yes (Fortinet native) | No (uses BGP) |
| **Performance** | [See Performance Factors](#performance-factors) | [See Performance Factors](#performance-factors) | [See Performance Factors](#performance-factors) | [See Performance Factors](#performance-factors) | [See Performance Factors](#performance-factors) |
| **Public Address Range Support** | Yes | Yes | Yes | Yes (Fortinet native integration) | Yes |
| **Supported Vendors** | All | All | Fortinet (native), Others (custom code) | Fortinet (native), Others (custom code) | BGP-capable vendors |
| **Use Case** | Dev/Test, Small workloads | High throughput via scaling | Production (zone-level resilience) | Production (regional resilience) | High throughput + regional resilience |
| **Licensing** | BYOL | BYOL | BYOL | BYOL | BYOL |
{: caption="Comparison of firewall deployment patterns" caption-side="bottom"}
{: caption="Comparison of firewall deployment patterns" caption-side="bottom"}

## Common network patterns
{: #common-network-patterns}

Firewall deployments in VPC are commonly implemented using standard network
patterns to control and inspect traffic flows.

### Transit VPC (Hub and Spoke)
{: #transit-vpc-pattern}

A centralized VPC that acts as a hub for routing traffic between multiple
spoke VPCs and on-premises networks. Firewalls are typically deployed in the
transit VPC to inspect and control traffic flows.

This pattern centralizes security and simplifies route management.

For more information, see [Securing multiple landing zones with a transit VPC and advanced security capabilities](/docs/pattern-transit-vpc?topic=pattern-transit-vpc-transit-vpc).

### Single VPC
{: #single-vpc-pattern}

Firewalls deployed within a single VPC to protect workloads and control
traffic flows within that VPC.

This pattern is simpler and best for small deployments or isolated workloads.

## Deployment options
{: #deployment-options}

{{site.data.keyword.vpc_short}} supports multiple deployment options to
address different availability and scalability requirements.

This is the simplest and most cost-effective deployment pattern.

### Standalone deployment
{: #standalone-deployment}

A single firewall instance without high availability. This deployment is
suitable for development, testing, or non-critical workloads.

#### Characteristics
{: #standalone-characteristics}

- Simplest deployment model
- No automatic failover
- Lower cost
- Any vendor supported

#### Available solutions
{: #standalone-solutions}

The following table outlines the available standalone firewall solutions from leading vendors, along with their corresponding products and catalog links.

| Vendor | Product | Catalog Link |
|--------|---------|--------------|
| Fortinet | FortiGate Next-Generation Firewall - Single VM | [Catalog](/catalog/content/ibm-fortigate-terraform-deploy-1f878ca9-069f-42ca-9ed9-5b461d4d5231-global) |
| Palo Alto | VM-Series Firewall - BYOL | [Catalog](/catalog/content/ibmcloud-vmseries-1.9-6470816d-562d-4627-86a5-fe3ad4e94b30-global) |
| Juniper | Next-Gen SASE Firewall - BYOL | [Catalog](/catalog/content/jnpr-nextgen-fw-vsrx-74b4b3ba-2a05-460d-afba-98e4d012f53a-global) |
| Check Point | CloudGuard Network Security Firewall | [Catalog](/catalog/content/check-point-cloudguard-network-security-firewall-with-threat-prevention-1f1f50fe-e41d-4715-9ba6-02d37d76596c-global) |
| F5 | BIG-IP Virtual Edition for VPC | [Catalog](/catalog/content/ibmcloud_schematics_bigip_multinic_declared-1.0-d33f1544-e938-478a-b0dd-d883370f08d0-global) |
{: caption="Available standalone firewall solutions" caption-side="bottom"}

#### Best for:
{: #standalone-best-for}

- Development and testing environments
- Non-critical workloads
- Cost-sensitive deployments
- Proof of concept projects

### Active/Active HA (Single Zone)
{: #active-active-single-zone}

Multiple firewall instances actively processing traffic simultaneously within
a single zone, using a Network Load Balancer for traffic distribution.

#### Characteristics
{: #active-active-single-zone-characteristics}

* Load balancing across multiple firewalls
* Higher throughput capacity
* Vendor-agnostic solution
* Uses Network Load Balancer (NLB) with Route mode

### Active/Passive HA (Single Zone)
{: #active-passive-single-zone}

Two firewall instances in an active/passive configuration within a single
availability zone. The passive instance takes over if the active instance
fails.

This deployment provides zone-level redundancy for production workloads.

#### Characteristics
{: #active-passive-single-zone-characteristics}

- Zone-level high availability
- Automatic failover using SDN Connector
- Supports virtual server instance and Bare Metal deployments
- Tested with Fortinet and Palo Alto

#### Available solutions
{: #active-passive-single-zone-solutions}

| Vendor | Product | Catalog Link |
|--------|---------|--------------|
| Fortinet | FortiGate Next-Generation Firewall - A/P HA | [Catalog](/catalog/content/ibm-fortigate-AP-HA-terraform-deploy-5dd3e4ba-c94b-43ab-b416-c1c313479cec-global) |
{: caption="Available Active/Passive HA (Single Zone) solutions" caption-side="bottom"}

#### Implementation options
{: #active-passive-single-zone-implementation}

##### Virtual server instances
{: #vsi-implementation}

* **Fortinet vFSA (FortiGate):**
   * [Transit VPC with FortiGate Solution Guide](/docs/pattern-transit-vpc-fortigate)
   * [FortiGate with SDN Connector](/docs/pattern-transit-vpc?topic=pattern-transit-vpc-transit-vpc#fortigate-with-SDN-connector)

### SDN Connector overview
{: #sdn-connector-overview}

The SDN Connector is a critical component that enables automatic failover in
Active/Passive HA configurations for virtual server instance-based
deployments. It monitors the firewall cluster and automatically updates VPC
routing tables when failover occurs.

Bare metal deployments do "not" use SDN Connector. They use VNI (Virtual
Network Interface) floating interfaces instead.
{: important}

#### Vendor support (virtual server instance only)
{: #sdn-connector-vendor-support}

* **Fortinet FortiGate**: Native SDN Connector integration included in IBM Cloud VPC images
* **Other Vendors**: Must implement custom automation or use manual failover processes

#### How it works
{: #sdn-connector-how-it-works}

1. **Monitoring**: Continuously monitors HA cluster state
1. **Detection**: Detects when active node changes
1. **API Integration**: Uses IBM Cloud VPC APIs to update routing
1. **Route Updates**: Redirects traffic to new active node

#### Failover process
{: #sdn-connector-failover-process}

1. Active node fails or becomes unavailable
1. Passive node detects failure and becomes active
1. SDN Connector detects the cluster state change
1. Connector queries VPC routing tables for routes with old active IP
1. Connector deletes each old route
1. Connector creates new routes pointing to new active node
1. Traffic automatically flows through new active node

#### Benefits
{: #sdn-connector-benefits}

- Automatic failover without manual intervention
- Fast recovery (typically seconds)
- No external monitoring required
- Integrated with firewall HA mechanism (Fortinet only)

### Active/Passive HA (multizone)
{: #active-passive-multizone}

Two firewall instances in an active/passive configuration across multiple
availability zones, providing regional-level high availability.

#### Characteristics
{: #active-passive-multizone-characteristics}

- Regional high availability
- Protection against zone failures
- Automatic failover across zones
- Currently optimized for Fortinet

#### Available solutions
{: #active-passive-multizone-solutions}

| Vendor | Product | Catalog Link |
|--------|---------|--------------|
| Fortinet | FortiGate Next-Generation Firewall - Cross Zone HA | [Catalog](/catalog/content/ibm-fortigate-cross-zone-ha-par-terraform-deploy-9a7c26d7-83c6-45bc-b145-e65d54c2d009-global) |
{: caption="Available Active/Passive HA (Multi-Zone) solutions" caption-side="bottom"}

#### Best for:
{: #active-passive-multizone-best-for}

- Mission-critical production workloads
- Applications requiring maximum availability
- Compliance requirements for regional resilience
- Disaster recovery scenarios

SDN Connector with cross-zone awareness automatically updates routing when
zone failure occurs.

### Cross-zone failover
{: #cross-zone-failover}

Cross-zone failover is more complex than single-zone failover due to
zone-specific routing requirements and the need to update zone bindings.

#### Vendor support
{: #cross-zone-vendor-support}

* **Fortinet FortiGate**: Native SDN Connector with cross-zone support and automatic public address range zone binding updates
* **Other Vendors**: Must implement custom automation for cross-zone failover

#### Failover process
{: #cross-zone-failover-process}

1. **Detection**: SDN Connector detects zone failure or active node change
1. **Route Updates**: Updates all routes pointing to old active node
1. **Zone Binding**: Updates route zone to match new active node's zone
1. **Public Address Range Updates**: If using Public Address Ranges for VPC,
   updates public address range zone binding (Fortinet only). Public address ranges support Public IPs across multiple zones.

#### Route update pattern
{: #cross-zone-route-update}

For each route pointing to old active node:

1. DELETE old route
1. CREATE new route with:

   - Same destination CIDR
   - New next_hop IP (new active node)
   - New zone (new active node's zone)

#### Key points
{: #cross-zone-key-points}

- Failover typically completes in seconds
- Brief traffic interruption during route updates
- Automatic recovery without manual intervention (Fortinet only)
- VPC routing table routes cannot be updated with new zone via PATCH (must
  use DELETE/CREATE)
- Floating IPs cannot move across zones (VPC limitation). Floating IPs support Public IP access within a single zone.

### Public Address Range integration
{: #par-integration}

Public address ranges enable public-facing applications to preserve source IP
addresses without NAT, while still routing through firewalls for inspection
and security.

#### What is Public Address Ranges for VPC?
{: #what-is-par}

* Public subnet bound to specific VPC and zone
* Used in routing tables with "Public Internet" as traffic source
* Preserves source IP (no NAT by VPC infrastructure)
* Firewall can perform NAT if needed for backend applications

#### Vendor support
{: #par-vendor-support}

* **Fortinet FortiGate**: Native Public Address Range integration with automatic zone binding updates during cross-zone failover (FortiOS 7.6.3+)
* **Other Vendors**: Can use public address ranges but must implement custom automation for zone binding updates

#### Use cases
{: #par-use-cases}

* Public-facing web applications requiring source IP visibility
* Services with IP-based access control or logging requirements
* Compliance requirements for IP address logging
* DDoS protection with source IP preservation

#### How public address ranges work with firewalls
{: #par-how-it-works}

1. A public address range is created and bound to a VPC and specific zone
1. Routing table configured with public address range CIDR as destination
1. Traffic from public internet matches public address range routes
1. Routes direct traffic through firewall as next hop
1. Firewall inspects and forwards to backend applications
1. Source IP preserved throughout the flow

#### Cross-zone failover with public address ranges (Fortinet only)
{: #par-cross-zone-failover}

When active firewall node moves to different zone, Fortinet's SDN Connector automatically:

1. Updates routing table routes (next_hop and zone)
1. Updates public address range zone binding to match new active node's zone
1. Ensures traffic continuity through new active node

#### Benefits
{: #par-benefits}

* Source IP preservation for security and compliance
* Transparent firewall operation for public traffic
* Automatic failover with public address range zone binding updates (Fortinet only)
* No application changes required

### Route Mode Network Load Balancer
{: #route-mode-nlb}

Route Mode is a special feature of {{site.data.keyword.cloud_notm}} Network
Load Balancer that enables transparent firewall deployments in Active/Active
configurations.

#### How Route Mode works
{: #route-mode-how-it-works}

- Preserves source and destination IP addresses (no NAT)
- Acts as "bump in the wire" for traffic inspection
- Distributes traffic across multiple firewall instances
- Maintains session affinity for stateful inspection

#### Traffic flow
{: #route-mode-traffic-flow}

```text
REQUEST:  Client → VPC Routing Table → NLB (Route Mode) → Firewall →
          Server
RESPONSE: Server → VPC Routing Table → NLB (Route Mode) → Same Firewall →
          Client
```

#### Key characteristics
{: #route-mode-characteristics}

- **Transparent Operation**: Client and server see each other's real IPs
- **No NAT**: Source and destination IPs preserved throughout flow
- **Session Persistence**: Return traffic uses same firewall instance
- **Load Distribution**: Traffic distributed across active firewall instances
- **Vendor Agnostic**: Works with any firewall vendor

#### Configuration requirements
{: #route-mode-configuration}

- Network Load Balancer with Route Mode enabled
- IP spoofing enabled on firewall interfaces
- Proper security group rules allowing traffic
- Routing tables configured to use NLB as next hop
- Firewall instances configured as backend pool members

#### Routing table configuration
{: #route-mode-routing-config}

Egress Routing Table (Client VPC):

- Destination: Server subnet CIDR
- Next Hop: NLB IP address
- Action: Deliver

Egress Routing Table (Server VPC):

- Destination: Client subnet CIDR
- Next Hop: NLB IP address
- Action: Deliver

#### Performance characteristics
{: #route-mode-performance}

- Lower latency than application load balancers
- Horizontal scaling by adding firewall instances
- Session persistence ensures stateful inspection works correctly
- Throughput scales with number of firewall instances
- Vendor-agnostic solution supports any firewall

#### Benefits
{: #route-mode-benefits}

- **Scalability**: Add firewall instances to increase capacity
- **High Availability**: Multiple active instances provide redundancy
- **Flexibility**: Works with any firewall vendor
- **Simplicity**: No complex BGP configuration required
- **Performance**: Efficient Layer 4 load balancing

For more information, see
[Virtual firewall appliances with network load balancer for traffic management](/docs/pattern-transit-vpc?topic=pattern-transit-vpc-transit-vpc#Virtual-firewall-Appliances-with-NLB).

### Active/Active HA (multizone)
{: #active-active-multizone}

Multiple firewall instances actively processing traffic across multiple
availability zones, using BGP for dynamic routing and failover.

#### Characteristics
{: #active-active-multizone-characteristics}

- Regional high availability with load balancing
- Highest throughput and resilience
- Requires BGP support
- Most complex deployment

#### Implementation
{: #active-active-multizone-implementation}

- Firewall must support BGP routing protocol
- Any vendor with BGP capability is supported
- For more information, see
  [Virtual firewall appliances with BGP Over GRE](/docs/pattern-transit-vpc?topic=pattern-transit-vpc-transit-vpc#Virtual-firewall-Appliances-with-BGP-over-GRE).

#### Best for:
{: #active-active-multizone-best-for}

- Enterprise-scale deployments
- Maximum throughput and availability requirements
- Complex routing scenarios
- Multi-region architectures

BGP over GRE tunnels provides dynamic routing and automatic failover across
zones.

## Licensing models
{: #licensing-models}

### Current state
{: #licensing-current}

Bring your own license (BYOL) is the current licensing model for
{{site.data.keyword.vpc_short}} firewalls.

### Future state
{: #licensing-future}

IBM-Licensed Fortinet Offerings will be available, providing:

- Simplified procurement through IBM
- Integrated billing
- IBM support for Firewall issues
- Pay-as-you-go pricing options

BYOL options will continue to be available for customers who prefer direct vendor relationships.
{: note}

## Migration from IBM Cloud Classic
{: #migration-from-classic}

### Classic infrastructure overview
{: #classic-infrastructure}

IBM Cloud Classic uses a Layer 2 network architecture with six primary firewall offerings:

#### Gateway Appliances (Still Available)
{: #gateway-appliances}

:   Virtual FortiGate (vFSA)

    See [Getting started with Fortigate Security Appliance](/docs/vfsa?topic=vfsa-getting-started-vfsa).

:    Virtual Juniper vSRX*

     See [Getting started with IBM Cloud Juniper vSRX](/docs/vsrx?topic=vsrx-getting-started-vsrx).

:    Virtual Router Appliance (Vyatta/VRA)

     See [Getting started with IBM Virtual Router Appliance](/docs/virtual-router-appliance).

For more information, see [Getting started with IBM Cloud Gateway Appliance](/docs/gateway-appliance?topic=gateway-appliance-getting-started-ga).

#### Deprecated physical firewalls
{: #deprecated-firewalls}

*  FortiGate 10G: See [Exploring Firewalls](/docs/fortigate-10g?topic=fortigate-10g-exploring-firewalls).
* Hardware Firewall (Shared): See [Getting started with Hardware Firewall (Shared)](/docs/hardware-firewall-shared).

### Key differences: Classic versus VPC
{: #classic-vs-vpc}

| Aspect | IBM Cloud Classic | IBM Cloud VPC |
|--------|-------------------|---------------|
| **Network Architecture** | Layer 2 | Layer 3 SDN |
| **Licensing** | IBM-licensed (except BYOL Gateway) | BYOL (IBM-licensed coming soon for Fortinet) |
| **High Availability** | A/P Single Data Center Pod | Multiple HA patterns |
| **Deployment Flexibility** | Physical and Bare Metal | Virtual (Virtual Server Instance and Bare Metal) |
{: caption="Key differences between Classic and VPC infrastructure" caption-side="bottom"}

### Migration considerations for gateway devices
{: #migration-considerations}

1. **Architecture Review:** VPC's Layer 3 SDN requires different network
   design patterns
1. **Licensing:** Plan for BYOL requirements or wait for IBM-licensed options
1. **High Availability:** Choose appropriate HA pattern based on requirements
1. **Automation:** Leverage Terraform and APIs for deployment
1. **Testing:** Thoroughly test failover scenarios in VPC environment

## Choosing the right deployment option
{: #choosing-deployment}

### Performance factors
{: #performance-factors}

Firewall performance in {{site.data.keyword.vpc_short}} is influenced by
multiple factors. Understanding these factors helps in selecting the
appropriate deployment configuration.

#### Firewall license
{: #firewall-license-performance}

* **vCPU Count**: Firewall vendor licenses typically limit throughput based
  on vCPU count
* **Gating Factor**: The license vCPU limit is usually the primary constraint
  on performance
* **Example**: A 4-vCPU firewall license will limit throughput regardless of
  virtual server instance profile size
* **Recommendation**: Match virtual server instance profile vCPU count to
  firewall license vCPU entitlement

#### Virtual server instance profile selection
{: #vsi-profile-selection}

* **Profile Size**: Larger profiles provide higher bandwidth caps (see [profile tables](/docs/vpc?topic=vpc-profiles))
* **Bandwidth Pooling** (Gen 4 profiles only): Network bandwidth is pooled across all interfaces, allowing flexible allocation
* **Pre-Gen 4 Profiles**: Bandwidth is equally divided across interfaces, not pooled
* **Example**: A bx4-32x128 profile has 64 Gbps bandwidth cap that can be pooled across all interfaces (Gen 4)

#### Network interface configuration
{: #network-interface-config}

* **Number of Interfaces**: More interfaces may impact available bandwidth per interface (pre-Gen 4)
* **Gen 4 Advantage**: Bandwidth pooling eliminates per-interface division
* **Recommendation**: Use Gen 4 profiles for firewall deployments when available

#### Network Load Balancer (Active/Active)
{: #nlb-active-active}

* **NLB Throughput**: Network Load Balancer has its own throughput limits
* **Route Mode**: Lower latency than application load balancers, efficient Layer 4 routing
* **Scaling**: Distribute load across multiple firewall instances for higher aggregate throughput

#### Bare Metal Servers
{: #bare-metal-performance}

* **High Network Throughput**: Dedicated hardware resources provide consistent high performance
* **VNI Floating Interfaces**: Automatic failover without SDN Connector overhead
* **Significant Limitations**: Requires manual hypervisor and VM configuration, monthly billing only, limited scaling flexibility, customer-managed OS and software
* **Recommendation**: Consider virtual server instance deployments first due to operational simplicity and flexibility

Bare metal servers provide dedicated hardware resources but require
significant manual configuration and management.

Failover Method

:   Uses VNI (Virtual Network Interface) floating interfaces instead of SDN
    Connector. The data interface automatically floats to the active node
    during failover.

Important Limitations

:   Consider the following limitations:

    - **Manual Configuration Required**: Hypervisor and all virtual machines must
  be manually configured and managed by customer
    - **Limited Flexibility**: Cannot scale out easily like virtual server
  deployments
    - **Billing**: Monthly billing only (no hourly billing option)
    - **Customer Managed**: Bare metal OS and all software are customer responsibility
    - **Complexity**: Requires expertise in hypervisor management and VM
  configuration

Technical Details

:   - **Key Difference**: Does "not" require SDN Connector - uses VNI floating
      interface technology
    - **Tested Vendors**: Fortinet (PCI Passthrough and macvtap), Palo Alto
      (macvtap)

For more information, see
[Virtual firewalls on VPC Bare Metal servers](/docs/pattern-transit-vpc?topic=pattern-transit-vpc-transit-vpc#Virtual-firewall-Appliances-on-VPC-Bare-Metals).

Virtual server instance deployments are recommended for most use cases due to
flexibility, ease of management, and hourly billing.
{: tip}

##### Best for:
{: #active-passive-single-zone-best-for}

* Production workloads requiring zone-level resilience
* Applications that can tolerate zone-level outages

##### Key recommendations
{: #performance-recommendations}

1. **Match License to Profile**: Ensure virtual server instance profile vCPU
   count matches or exceeds firewall license vCPU entitlement
1. **Use Gen 4 Profiles**: Bandwidth pooling provides better flexibility for
   multi-interface firewalls
1. **Start with virtual server instances**: Virtual server instance
   deployments offer better flexibility, easier management, and hourly billing
1. **Test Performance**: Validate actual throughput meets requirements before
   production deployment

#### Gen 4 virtual server instance profile examples
{: #gen4-vsi-profiles}

Balanced Profiles (bx4):

| Profile | vCPU | Memory (GiB) | Bandwidth Cap (Gbps) |
|---------|------|--------------|----------------------|
| bx4-8x32 | 8 | 32 | 16 |
| bx4-16x64 | 16 | 64 | 32 |
| bx4-32x128 | 32 | 128 | 64 |
| bx4-48x192 | 48 | 192 | 96 |
| bx4-64x256 | 64 | 256 | 128 |
{: caption="Gen 4 balanced virtual server instance profiles (bx4)" caption-side="bottom"}

Gen 4 profiles feature bandwidth pooling across all interfaces. For complete
profile details, see [General purpose instance profiles - Intel Gen 4](/docs/vpc?topic=vpc-general-purpose-vsi-profiles-gen4-intel).
{: note}

### Cost considerations
{: #cost-considerations}

- **Standalone:** Lowest cost, no redundancy
- **Single Zone HA:** Moderate cost, good balance
- **Multi-Zone HA:** Higher cost, maximum availability
- **Virtual server instance vs Bare Metal:** Virtual server instances offer
  hourly billing and operational flexibility; bare metal requires monthly
  billing and manual management

## Next steps
{: #next-steps}

* [Transit VPC Pattern](/docs/pattern-transit-vpc?topic=pattern-transit-vpc-transit-vpc)
* [VPC Networking Overview](/docs/vpc?topic=vpc-about-networking-for-vpc)
* [IBM Cloud Catalog - Network Security](/catalog?category=network_security)
* [Getting help and support](/docs/get-support)
