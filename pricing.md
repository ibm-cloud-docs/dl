---

copyright:
  years: 2020, 2023
lastupdated: "2023-02-02"

keywords: pricing, direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Pricing for {{site.data.keyword.dl_full_notm}} (OUTDATED - FOR REFERENCE ONLY)
{: #pricing-for-ibm-cloud-dl}

Pricing for {{site.data.keyword.dl_full}} offerings is consistent for equivalent regions and bandwidth, as shown in the following monthly pricing table.
{: shortdesc}

{{site.data.keyword.dl_short}} pricing does NOT include any additional charges by service providers to enable connectivity to {{site.data.keyword.cloud_notm}}.
{: important}

## Arranging for {{site.data.keyword.dl_short}} connectivity
{: #arranging-for-dl-conectivity}

You, the customer, must arrange connectivity and billing with your service providers, independently of {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.dl_short}} Dedicated creates a Letter Of Authorization / Connecting Facility Assignment (LOA/CFA) which is usable by any service provider who can reach the Meet Me Room that is specified on that LOA/CFA. The provider who is connecting to the LOA/CFA must include pricing for the cross-connect in their quote to you. {{site.data.keyword.cloud_notm}} does not order cross-connects on behalf of any customer.

{{site.data.keyword.dl_short}} Connect uses pre-established physical connections to support virtual connections that Do Not need a LOA/CFA, but do require ordering from the Service Provider.

## Pricing for port charges
{: #pricing-for-dl-port-charges}

The following tables list the pricing for metered and unmetered port charges.

### Unmetered
{: #pricing-for-dl-port-charges-unmetered}

Select a tab in the table to view pricing for Direct Link offerings:

| Region | 50 Mbps | 100 Mbps | 200 Mbps | 500 Mbps | 1 Gbps | 2 Gbps | 5 Gbps |
|----|----|----|----|----|----|----|----|
| US | $100 | $150 | $300 | $650 | $1,199 | $1,999 | $3,750 |
| Canada / Amsterdam | $103 | $155 | $309 | $670 | $1,235 | $2,059 | $3,863 |
| London / Norway | $107 | $161 | $321 | $696 | $1,283 | $2,139 | $4,013 |
| Paris / Frankfurt / Milan / Korea | $110 | $165 | $330 | $715 | $1,319 | $2,199 | $4,125 |
| Japan / Singapore / Hong Kong | $113 | $170 | $339 | $735 | $1,355 | $2,259 | $4,238 |
| Australia / Brazil / India | $120 | $180 | $360 | $780 | $1,439 | $2,399 | $4,500|
{: class="simple-tab-table"}
{: caption="Table 1. Direct Link Connect" caption-side="bottom"}
{: #simpletabtable1}
{: tab-title="Connect"}
{: tab-group="IAM-simple"}

| Region | 1 Gbps | 2 Gbps | 5 Gbps | 10 Gbps |
|----|----|----|----|----|
| US | $1,199 | $1,999 | $3,750 | $4,999 |
| Canada/Amsterdam | $1,235 | $2,059 | $3,863 | $5,149 |
| London / Norway| $1,283 | $2,139 | $4,013 | $5,349 |
| Paris / Frankfurt / Milan / Korea | $1,319 | $2,199 | $4,125 | $5,499 |
| Japan / Singapore / Hong Kong | $1,355 | $2,259 | $4,238 | $5,649 |
| Australia / Brazil / India | $1,439 | $2,399 | $4,500| $5,999 |
{: #simpletabtable2}
{: caption="Table 2. Direct Link Dedicated" caption-side="bottom"}
{: tab-title="Dedicated"}
{: tab-group="IAM-simple"}
{: class="simple-tab-table"}

### Metered
{: #pricing-for-dl-port-charges-metered}

Provider speeds greater than 10 Gbps for Direct Link Connect incur metered billing only.
{: important}

| Speed | Global |
|----|----|
|  50 Mbps (Direct Link Connect only) |   $40 |
| 100 Mbps (Direct Link Connect only) |   $45 |
| 200 Mbps (Direct Link Connect only) |   $60 |
| 500 Mbps (Direct Link Connect only) |  $150 |
|   1 Gbps |  $250 |
|   2 Gbps |  $500 |
|   5 Gbps |$1,200 |
|  10 Gbps (Direct Link Dedicated only) |$1,800 |
{: caption="Table 2. {{site.data.keyword.dl_short}} metered port charges" caption-side="bottom"}

Metered port fee pricing is determined by the bandwidth speed of the port.
{: note}

## Pricing for metered data transfer charges
{: #metered-data-transfer-charge}

The following table lists the pricing for metered data transfer charges.

| Tier | US, Canada & EU | Asia Pacific | Brazil |
|----|----|----|----|
| Per GB | $0.025 | $0.050 | $0.140 |
{: caption="Table 3. {{site.data.keyword.dl_short}} metered data transfer charges" caption-side="bottom"}

Data transfer is for egress only, and varies based on region. Inbound data transfer to IBM Cloud is free.
{: note}

## Pricing for routing charges
{: #pricing-for-global-routing-charges}

The following sections list the pricing for local and global routing charges.

### Local routing charges
{: #pricing-local-routing-charges}

Local routing is the default routing option. It provides access to data centers within the same market as the {{site.data.keyword.dl_short}} PoP. There's no charge for Local routing.

### Global routing charges
{: #pricing-global-routing-charges}

Global routing expands access to include all {{site.data.keyword.cloud_notm}} data centers globally. There's no charge for global routing on Direct Link. However, Direct Link on Classic will still carry the global routing charge.

Details on the markets, changing billing options, and other considerations can be found in our [FAQs](/docs/dl?topic=dl-faqs).
{: note}
