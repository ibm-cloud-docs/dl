---

copyright:
  years: 2021
lastupdated: "2021-9-09"

keywords:  

subcollection: dl

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:term: .term}  
{:generic: data-hd-programlang="generic"}
{:download: .download}  
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Setting up Bidirectional Forwarding Detection (BFD)
{: #dl-bfd}

Bidirectional Forwarding Detection (BFD) quickly detects faults in a network between two routers or switches connected by a link. It provides a single, standardized method for failover detection at any protocol layer over any media. BFD also provides a way for network administrators to detect forwarding-path failures at a uniform rate, rather than the variable rates of different routing protocol hello mechanisms. Network profiling and planning is easier, and reconvergence time is predictable, consistent, and significantly faster.

BFD support comes pre-enabled with your direct link. However, BFD doesn’t start working until you activate the feature during direct link creation, or on an existing direct link. No prerequisites are required. Simply configure this feature with the following values:

* Interval – The interval is the minimum time (in milliseconds) expected to occur between when the local routing device sends BFD hello packets and the reply from its neighbor. This value can range from 300 to 255,000 milliseconds.
* Multiplier – The multiplier is the number of times that a hello packet is missed before BFD declares the neighbor down. This value can range from 1 to 255. The default multiplier value is 3. 

## Related link
{: #bfd-related-link}

[Activating and deactivating Bidirectional Forwarding Detection (BFD)](/docs/dl?topic=dl-activate-deactivate-bfd)
