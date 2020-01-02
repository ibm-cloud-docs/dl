---

copyright:
  years: 2019
lastupdated: "2019-12-15"

keywords: direct link, IAM, permissions, access

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

#  Identity and Access Management roles and actions
{: #iam}

{{site.data.keyword.cloud}} Direct Link Dedicated enables connectivity between customer on-premises resources to {{site.data.keyword.cloud_notm}} resources hosted in classic and Virtual Private Cloud (VPC) infrastructures, including second-generation compute resources.
{: shortdesc}

{{site.data.keyword.cloud_notm}} Direct Link Dedicated uses {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) platform access roles and IAM service access roles to manage access to the service's resources. IAM access roles allow account administrators to assign different levels of permission for calling the service's APIs and accessing the UI. The following tables provide example actions that you can take against the Direct Link service and its resources depending on a user's assigned roles.

## Service-access roles

Direct Link Dedicated supports Reader, Writer, and Manager service-access roles.
{: shortdesc}

| Role | Description of Actions | Example Actions |
|---|---|---|
| Reader | Performs actions that don't change the state of resources. |<ul><li>List gateways</li><li>Get gateways</li><li>List a gateway's virtual connections</li><li>View a gateway's virtual connections</li><li>Retrieve gateway-related information (completion notice/letter of authorization)</li><li>View incoming connection requests&#8902; </li></ul>
| Writer and Manager | Performs all actions, including managing gateways and virtual connections. |<ul><li>Create gateway</li><li>Delete gateway</li><li>Edit gateway</li><li>Add a virtual connection to a gateway&#8902;  </li> <li>Remove a virtual connection from a gateway&#8902; </li><li>Edit a virtual connection |                     |
{: caption="Table 1. IAM service-access user roles and actions" caption-side="top"}

&#8902; To add or remove virtual connections to VPCs, or to accept/reject a connection request, the user must also have Editor or Administrator platform-access role permissions to the VPC. See [VPC: Getting started with IAM](/docs/vpc?topic=vpc-iam-getting-started) for more information.

## Platform-access roles

Direct Link Dedicated supports the Administrator platform-access role.
{: shortdesc}

| Role | Description of Actions | Example Action
|---|---|---|
| Administrator | Allows a user to assign Direct Link IAM access policies to other users. | Update user access policies for the service. |                 |
{: caption="Table 2. IAM platform-access user role and actions" caption-side="top"}


## Viewing Direct Link resources in the Resource list

To view Direct Link resources in the {{site.data.keyword.cloud_notm}} Resource list, users need an IAM policy for the Direct Link service. Direct Link resource-type specific policies are not sufficient.
