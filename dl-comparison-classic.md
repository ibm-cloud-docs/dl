---

copyright:
  years: 2021, 2024
lastupdated: "2024-11-22"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Feature comparison between Direct Link versions
{: #dl-comparison-classic}

Review feature support for Direct Link on Classic offerings versus Direct Link.
{: shortdesc}

| **Feature** | **Direct Link on Classic** | **Direct Link** |
|-----|-----|-----|
| Locations | All IBM Cloud data centers and PoP locations have Direct Link on Classic support. | All MZRs have Direct Link offering support. Single-campus multizone region support is being rolled out on a location-by-location basis. |
| 100G NNI | No 100G NNI support. | Business case justification is required in roadmap for MZR’s and associated POP’s pending business/finance approval. |
| Account in VRF | VRF migration is required. | If the account is used for VPC connectivity only, there is no need to migrate to VRF. If SoftLayer classic network connectivity is required, then the account needs a VRF migration. |
| BGP authentication. | You can open an IBM Support ticket to enable this feature for all Direct Link on Classic offerings. | Supported for Dedicated and Connect offerings through automation. Need to store the MD5 secret in Key Protect or an HPCS instance in the customer account. |
| Default BGP IP address range for automation | `10.254.0.0/16` | `169.254.0.0/16` |
| Manual IP address range supported | None | `172.16.0.0/12`, `192.168.0.0/16`, `10.254.0.0/16`, any public IP addresses |
| BGP ASN supported | Allowed to use any ASN outside these blocked ranges: Allowed to use any ASN outside these blocked ranges: `0`, `13884`, `36351`, `64512`, `64513`, `65100`, `65201 – 65234`, `65402 – 65433`, `65500`, and `4201065000 – 4201065999` | 2-byte range: `1` - `64495` or `64999`  \n 2-byte or 4-byte range: `131072` - `4199999999`  \n 4-byte range: `4201000000` - `4294967294`  \n  Excluded ASNs: `0`, `13884`, `36351`, `64512`, `64513`, `65100`, `65201 – 65234`, `65402 – 65433`, `65500`, `65516`, `65519`, `65521`, `65531`, and `4201065000 – 4201065999`.
| Billing | Supports only monthly flat rate billing. | Metered based on the data utilization and unmetered flat rate support. |
| VPC connectivity | No VPC connectivity — can connect only to SoftLayer classic networks. | Supports connectivity to multiple VPCs and connects to SoftLayer classic networks. |
| Cross-account connectivity | Allows classic network connectivity within the account only.  | Allows VPC connectivity between IBM Cloud accounts, except for classic-access VPCs (see Adding a cross-account (VPC only) connection for details). |
| Bring Your Own IP (BYIOP) | No BYOIP support. | Supports BYOIP for nonoverlapping RFC-1918 IP ranges between VPC networks and on-premises networks (see [Routing considerations for IANA-registered IP assignments](/docs/vpc?topic=vpc-interconnectivity) for details). |
| Pricing | Global routing has a monthly flat rate charge. | Free global routing. |
| Automation | Full automation for Equinix Exchange and Colt Connect offerings. The rest of the ordering process is partially automated and requires manual configuration. | Automation for Dedicated and Connect offerings. Fully automated single-click ordering experience with the providers Equinix, Packet Fabric, Cologix, British Telecom and DE-CIX. For automation information, see [Partner-specific instructions](/docs/dl?topic=dl-how-to-order-ibm-cloud-dl-connect#instructions-partner). |
| Connectivity between Direct Link and Transit Gateway | Not supported. | All MZRs have Direct Link offering support. |
| Bidirectional Forwarding Detection (BFD) | You can open an IBM Support case to enable this feature for all Direct Link on Classic offerings. | All MZRs have Direct Link offering support. |
| Update BGP ASN and IP | You can open an IBM Support ticket to enable this feature for all Direct Link on Classic offerings. | All MZRs have Direct Link offering support. |
{: caption="Feature comparison between Direct Link versions" caption-side="bottom"}
