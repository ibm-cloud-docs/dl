---

copyright:
  years: 2020, 2024
lastupdated: "2024-07-18"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Securing your data in {{site.data.keyword.dl_short}}
{: #mng-data}

{{site.data.keyword.dl_short}} does not store any customer data. IBM does not encrypt data that is transmitted through a direct link gateway.

Data about your specific {{site.data.keyword.dl_short}} configuration is encrypted in transit and at rest. Configuration data is deleted upon your request through API or User Interface.
{: shortdesc}

## How your data is stored and encrypted in {{site.data.keyword.dl_short}}
{: #data-storage}

All interaction with {{site.data.keyword.dl_short}} from clients is encrypted. For example, when a client uses an API or interacts with the service through a user interface to configure gateways and connections, all such interactions are fully end-to-end encrypted. Likewise, data elements that are related to the clients' configuration are encrypted in transit and at rest. No personal or sensitive data is stored, processed, or transmitted. Data at rest is stored in an encrypted database.

However, the result of using {{site.data.keyword.dl_short}} is to join customer networks together. After networks are joined, for example from on-premises networks to a VPC, the encryption of data that clients choose to transmit across the network is the client's responsibility.

## Protecting your sensitive data in {{site.data.keyword.dl_short}}
{: #data-encryption}

All data related to {{site.data.keyword.dl_short}}'s configuration is not considered as sensitive data. The configuration data is encrypted at rest at the database level. The {{site.data.keyword.dl_short}} offering does not manage customer-managed keys. Therefore, Key Protect and Hyper Protect Crypto Services are not used.

### About customer-managed keys
{: #about-encryption}

The {{site.data.keyword.dl_short}} offering does not manage customer-managed keys. Therefore, Key Protect and Hyper Protect Crypto Services are not used.

### Enabling customer-managed keys for {{site.data.keyword.dl_short}}
{: #using-byok}

The {{site.data.keyword.dl_short}} offering does not manage customer-managed keys. Therefore, Key Protect and Hyper Protect Crypto Services are not used.

### Working with customer-managed keys for {{site.data.keyword.dl_short}}
{: #working-with-keys}

The {{site.data.keyword.dl_short}} offering does not manage customer-managed keys. Therefore, Key Protect and Hyper Protect Crypto Services are not used.

## Deleting your data in {{site.data.keyword.dl_short}}
{: #data-delete}

The {{site.data.keyword.dl_short}} configuration is deleted on request through the API or user interface.

### Deleting {{site.data.keyword.dl_short}} instances
{: #service-delete}

The {{site.data.keyword.dl_short}} configuration is deleted on request through the API or user interface.

### Restoring deleted data for {{site.data.keyword.dl_short}}
{: #data-restore}

Direct Link does not support the restoration of deleted data.
