---

copyright:
  years: 2018, 2020
lastupdated: "2020-09-23"

keywords: migration, direct link connect, migrating from beta release, move to paid plan

subcollection: dl

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:preview: .preview}
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

# Migrating Direct Link Connect gateways
{: #migration}

23 September 2020: If you participated in the beta release, you must migrate to a standard paid plan to continue using instances that you created during the beta. Any instances that continue to use the beta plan for this service beyond the 30 days notice of general availability are subject to deletion.  
{: preview}

To migrate Direct Link Connect gateways to a standard, paid plan before the 30-day window expires, enter the following command:

```
ibmcloud resource service-instance-update ( NAME | ID ) [--service-plan-id SERVICE_PLAN_ID]
```
{: pre}

For example:

```
ibmcloud resource service-instance-update nwk-stdplan --service-plan-id 3341e514-f13c-469b-800c-03c7e827fc7b
```

For information about opening an IBM Support case, or about support levels and ticket severities, see [Getting help and support](/docs/dl?topic=dl-getting-help-and-support).
