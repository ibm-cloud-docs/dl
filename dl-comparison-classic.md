---

copyright:
  years: 2021, 2026
lastupdated: "2026-05-10"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Feature comparison between Direct Link versions
{: #dl-comparison-classic}

Review feature support for Direct Link on Classic (1.0), Direct Link (2.0), and Direct Link Dedicated with MACsec
{: shortdesc}

| **Feature** | **Direct Link on Classic** | **Direct Link** | **Direct Link Dedicated with MACsec** |
|-----|-----|-----|-----|
| Locations | All IBM Cloud data centers and PoP locations have Direct Link on Classic support. | All MZRs have Direct Link offering support. Single-campus multizone region support is being rolled out on a location-by-location basis. | Available only in selected IBM Cloud PoP and data center locations with MACsec-capable hardware. |
| 100G NNI | No 100G NNI support. | Business case justification is required in roadmap for MZR’s and associated POP’s pending business/finance approval. | No announced 100G MACsec support currently. MACsec is currently available on Direct Link Dedicated deployments up to 10 Gbps. |
| Account in VRF | VRF migration is required. | If the account is used for VPC connectivity only, there is no need to migrate to VRF. If SoftLayer classic network connectivity is required, then the account needs a VRF migration. | Same as Direct Link. |
| BGP authentication | You can open an IBM Support case to enable this feature for all Direct Link on Classic offerings. | Supported for Dedicated and Connect offerings through automation. Need to store the MD5 secret in Secrets Manager, Key Protect, or an HPCS instance in the customer account. | Supported together with MACsec. CAK secrets must be stored in Secrets Manager or HPCS. |
| Default BGP IP address range for automation | `10.254.0.0/16` | `169.254.0.0/16` | `169.254.0.0/16` |
| Manual IP address range supported | None | `172.16.0.0/12`, `192.168.0.0/16`, `10.254.0.0/16`, any public IP addresses | Same as Direct Link. |
| BGP ASN supported | Allowed to use any ASN outside these blocked ranges: `0`, `13884`, `36351`, `64512`, `64513`, `65100`, `65201 – 65234`, `65402 – 65433`, `65500`, and `4201065000 – 4201065999` | The router supports public and private ASNs, including both 2-byte and 4-byte values (`1` to `4,294,967,294`), except for the excluded ASNs listed. | Same as Direct Link. |
| Billing | Supports only monthly flat rate billing. | Metered based on the data utilization and unmetered flat rate support. | Same as Direct Link Dedicated pricing. |
| VPC connectivity | No VPC connectivity — can connect only to SoftLayer classic networks. | Supports connectivity to multiple VPCs and connects to SoftLayer classic networks. | Supports connectivity to multiple VPCs and classic networks with Layer 2 encryption using MACsec. |
| Cross-account connectivity | Allows classic network connectivity within the account only. | Allows VPC connectivity between IBM Cloud accounts, except for classic-access VPCs. | Same as Direct Link. |
| Bring Your Own IP (BYOIP) | No BYOIP support. | Supports BYOIP for nonoverlapping RFC-1918 IP ranges between VPC networks and on-premises networks. | Same as Direct Link. |
| Pricing | Global routing has a monthly flat rate charge. | Free global routing. | Free global routing. MACsec itself is enabled as part of Direct Link Dedicated. |
| Automation | Full automation for Equinix Exchange and Colt Connect offerings. The rest of the ordering process is partially automated and requires manual configuration. | Automation for Dedicated and Connect offerings. Fully automated single-click ordering experience with several providers. | Automated ordering for Direct Link Dedicated with MACsec, including MACsec policy and CAK configuration integration with Secrets Manager/HPCS. |
| Connectivity between Direct Link and Transit Gateway | Not supported. | All MZRs have Direct Link offering support. | Same as Direct Link. |
| Bidirectional Forwarding Detection (BFD) | You can open an IBM Support case to enable this feature for all Direct Link on Classic offerings. | All MZRs have Direct Link offering support. | Same as Direct Link. |
| Update BGP ASN and IP | You can open an IBM Support case to enable this feature for all Direct Link on Classic offerings. | All MZRs have Direct Link offering support. | Same as Direct Link. |
| Encryption | No native Layer 2 encryption support. | No native Layer 2 encryption support. | Supports IEEE 802.1AE MACsec encryption with hardware-based encryption, replay protection, and integrity validation. |
| Key management | Not supported. | BGP MD5 secret can be stored in Secrets Manager, Key Protect, or HPCS. | MACsec CAK secrets must be stored in IBM Secrets Manager or Hyper Protect Crypto Services (HPCS). |
{: caption="Feature comparison between Direct Link versions" caption-side="bottom"}
