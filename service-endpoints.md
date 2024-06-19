---

copyright:
  years: 2024
lastupdated: "2024-01-08"
keywords: api

subcollection: dl


---

{{site.data.keyword.attribute-definition-list}}



_Make sure that you use the following title for your topic._

# Using service endpoints to privately connect to Direct Link
{: #service-endpoints}



To ensure that you have enhanced control and security over your data when you use Direct Link, you have the option of using private routes to {{site.data.keyword.cloud}} service endpoints. Private routes are not accessible or reachable over the internet. By using the {{site.data.keyword.cloud_notm}} private service endpoints feature, you can protect your data from threats from the public network and logically extend your private network.
{: shortdesc}

_Required: Document any customer data that goes over public routes even with the IBM Cloud service endpoints feature enabled using a connection over private routes. For example, if your service sends customer data to a data-service using a public route or sends customer logs using public routes to LogDNA that should be documented._




## Before you begin
{: #prereq-service-endpoint}

Document that users can connect to your service over a private network by using IBM Cloud private service endpoints. Point to the core documentation about how to enable the capability in their account, and then cover any details that are specific to your service about using it, for example:

You must first enable virtual routing and forwarding in your account, and then you can enable the use of IBM Cloud private service endpoints. For more information about setting up your account to support the private connectivity option, see [Enabling VRF and service endpoints](/docs/account?topic=account-vrf-service-endpoint).

## Setting up service endpoints for Direct Link
{: #endpoint-setup}

Review the following example: https://cloud.ibm.com/docs/secrets-manager?topic=secrets-manager-service-connection Depending on how your service supports and requires users to set up this capability, document the steps to ensure a user can successfully connect over the private service endpoint. You can use separate headers to break this into sections if the process includes a lot of steps or use numbered steps for a less lengthy process.

High level steps typically covered are: Add a private network endpoint, view your endpoint URL, and modifying your apps to use the new endpoint

## Disabling public service endpoints for for _servicename_
{: #endpoint-disable}

This section will not apply to all services. It does apply to compute services, databases, and Cloud Object Storage at this time.

Review the following example: https://cloud.ibm.com/docs/metrics-router?topic=metrics-router-service-endpoints Depending on how and if your service supports users to disable public endpoints, document the steps for disabling a public endpoint to ensure a user can connectly over only the private endpoint, if this is an option. You can use separate headers to break this into sections if the process includes a lot of steps or use numbered steps for a less lengthy process.
