---

copyright:
  years: 2024
lastupdated: "2024-09-20"
keywords: api

subcollection: dl


---

{{site.data.keyword.attribute-definition-list}}

 

# Using service endpoints to privately connect to Direct Link
{: #service-endpoints}



To enhance control and security over your data when you use Direct Link, you can use private routes to {{site.data.keyword.cloud}} service endpoints. Private routes are not accessible or reachable over the internet. By using the {{site.data.keyword.cloud_notm}} private service endpoints feature, you can protect your data from threats from the public network and logically extend your private network.
{: shortdesc}

_Required: Document any customer data that goes over public routes even with the IBM Cloud service endpoints feature enabled that uses a connection over private routes. For example, if your service sends customer data to a data-service using a public route or sends customer logs that use public routes to LogDNA, document it._




## Before you begin
{: #prereq-service-endpoint}

Document that users can use IBM Cloud private service endpoints to connect to your service over a private network. Point to the core documentation about how to enable the capability in their account, and then cover any details that are specific to your service about using it, for example:

First enable virtual routing and forwarding in your account, and then you can enable the use of IBM Cloud private service endpoints. For more information about setting up your account to support the private connectivity option, see [Enabling VRF and service endpoints](/docs/account?topic=account-vrf-service-endpoint).

## Setting up service endpoints for Direct Link
{: #endpoint-setup}

Review the following example: https://cloud.ibm.com/docs/secrets-manager?topic=secrets-manager-service-connection Depending on how your service supports and requires users to set up this capability, document the steps to make sure that a user can successfully connect over the private service endpoint. You can use separate headers if the process includes many steps or use numbered steps for a less lengthy process.

High-level steps that are typically covered are: Add a private network endpoint, view your endpoint URL, and modifying your apps to use the new endpoint

## Disabling public service endpoints for Direct Link
{: #endpoint-disable}

Does not apply to all services. It does apply to compute services, databases, and Cloud Object Storage.

Review the following example: https://cloud.ibm.com/docs/metrics-router?topic=metrics-router-service-endpoints Depending on how and if your service supports users to disable public endpoints, document the steps for disabling a public endpoint to make sure that a user can connect over only the private endpoint. You can use separate headers if the process includes many steps or use numbered steps for a less lengthy process.
