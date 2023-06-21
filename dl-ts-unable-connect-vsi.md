---

copyright:
  years: 2023
lastupdated: "2023-06-19"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# If my Direct Link is established, why can't I connect to my VPC virtual server instance?
{: #troubleshoot-unable-connect-vsi}
{: troubleshoot}
{: support}

My Direct Link is established, but I am still unable to connect to my VPC virtual server instance.
{: shortdesc}

Because Direct Link BGP is in an established state, on-prem and VPC routes are shown in the route report; however, on-prem customers cannot reach the VPC virtual server instance.
{: tsSymptoms}

The virtual server instance is powered off because the VPC is in suspended state.
{: tsCauses}

Verify that both your virtual server instance and VPC are not in suspended state. If they are in suspended state, you are unable to connect to them regardless of the BGP status and routes.
{: tsResolve}
