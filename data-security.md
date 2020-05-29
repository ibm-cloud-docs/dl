---

copyright:
  years: 2020
lastupdated: "2020-02-24"

keywords: data encryption in Direct Link, data storage for Direct Link, bring your own keys for Direct Link, BYOK for Direct Link, key management for Direct Link, key encryption for Direct Link, personal data in Direct Link, data deletion for Direct Link, data in Direct Link, data security in Direct Link

subcollection: dl

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}

# Securing your data in Direct Link
{: #mng-data}

All interaction with Direct Link from clients is encrypted. The Direct Link configuration is deleted on request through the API or user interface.

{: shortdesc}

## How your data is stored and encrypted in Direct Link
{: #data-storage}

All interaction with Direct Link from clients is encrypted. For example, when a client uses an API or interacts with the service via User Interface to configure gateways and connections, all such interactions are fully end-to-end encrypted. Likewise, data elements related to the clients' configuration are encrypted in transit and at rest. No personal or sensitive data is stored, processed, or transmitted. Data at rest is stored in an encrypted database.

However, the result of using Direct Link is to join customer networks together. Once networks are joined together, for example from one VPC to another, the encryption of data that clients choose to transmit across the network is the client's responsibility.

## Protecting your sensitive data in Direct Link
{: #data-encryption}

All data related to a Direct Link configuration is not considered as sensitive data. The configuration data is encrypted at rest at the database level. No customer-managed keys are managed by the Direct Link offering. Therefore, neither Key Protect nor Hyper Protect Crypto Services are used.

### About customer-managed keys
{: #about-encryption}

No customer-managed keys are managed by the Direct Link offering. Therefore, neither Key Protect nor Hyper Protect Crypto Services are used.

### Enabling customer-managed keys for Direct Link
{: #using-byok}

No customer-managed keys are managed by the Direct Link offering. Therefore, neither Key Protect nor Hyper Protect Crypto Services are used.

### Working with customer-managed keys for Direct Link
{: #working-with-keys}

No customer-managed keys are managed by the Direct Link offering. Therefore, neither Key Protect nor Hyper Protect Crypto Services are used.

## Deleting your data in Direct Link
{: #data-delete}

The Direct Link configuration is deleted on request through the API or user interface.

### Deleting Direct Link instances
{: #service-delete}

The Direct Link configuration is deleted on request through the API or user interface.

### Restoring deleted data for Direct Link
{: #data-restore}

Direct Link does not support the restoration of deleted data.
