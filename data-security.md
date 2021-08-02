---

copyright:
  years: 2020
lastupdated: "2020-02-24"

keywords:  

subcollection: dl

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}

# Securing your data in {{site.data.keyword.dl_short}}
{: #mng-data}

{{site.data.keyword.dl_short}} does not store any customer data. Data transmitted through a transit gateway is not encrypted by IBM.

Data about your specific {{site.data.keyword.dl_short}} configuration are encrypted in transit and at rest. {{site.data.keyword.dl_short}} configuration data is deleted upon your request through API or User Interface.
{: shortdesc}

## How your data is stored and encrypted in {{site.data.keyword.dl_short}}
{: #data-storage}

All interaction with {{site.data.keyword.dl_short}} from clients is encrypted. For example, when a client uses an API or interacts with the service via User Interface to configure gateways and connections, all such interactions are fully end-to-end encrypted. Likewise, data elements related to the clients' configuration are encrypted in transit and at rest. No personal or sensitive data is stored, processed, or transmitted. Data at rest is stored in an encrypted database.

However, the result of using {{site.data.keyword.dl_short}} is to join customer networks together. Once networks are joined together, for example from one VPC to another, the encryption of data that clients choose to transmit across the network is the client's responsibility.

## Protecting your sensitive data in {{site.data.keyword.dl_short}}
{: #data-encryption}

All data related to {{site.data.keyword.dl_short}}'s configuration is not considered as sensitive data. The configuration data is encrypted at rest at the database level. No customer-managed keys are managed by the {{site.data.keyword.dl_short}} offering. Therefore, neither Key Protect nor Hyper Protect Crypto Services are used.

### About customer-managed keys
{: #about-encryption}

No customer-managed keys are managed by the {{site.data.keyword.dl_short}} offering. Therefore, neither Key Protect nor Hyper Protect Crypto Services are used.

### Enabling customer-managed keys for {{site.data.keyword.dl_short}}
{: #using-byok}

No customer-managed keys are managed by the {{site.data.keyword.dl_short}} offering. Therefore, neither Key Protect nor Hyper Protect Crypto Services are used.

### Working with customer-managed keys for {{site.data.keyword.dl_short}}
{: #working-with-keys}

No customer-managed keys are managed by the {{site.data.keyword.dl_short}} offering. Therefore, neither Key Protect nor Hyper Protect Crypto Services are used.

## Deleting your data in {{site.data.keyword.dl_short}}
{: #data-delete}

The {{site.data.keyword.dl_short}} configuration is deleted on request through the API or user interface.

### Deleting {{site.data.keyword.dl_short}} instances
{: #service-delete}

The {{site.data.keyword.dl_short}} configuration is deleted on request through the API or user interface.

### Restoring deleted data for {{site.data.keyword.dl_short}}
{: #data-restore}

{{site.data.keyword.dl_short}} does not support the restoration of deleted data.
