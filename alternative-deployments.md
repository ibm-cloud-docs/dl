---

copyright:
  years: 2018, 2024
lastupdated: "2024-10-09"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Alternatives for your Direct Link Connect deployment
{: #alternatives-for-your-ibm-cloud-direct-link-deployment}

Describes alternatives that you can choose for your Direct Link Connect deployments.
{: shortdesc}

The default deployments of Direct Link Connect do not include redundant configuration, although they can be deployed diversely on discrete routers.

Many customers choose to create redundant deployments by setting up an extra Direct Link connection. The following diagrams illustrate some schematic representations of alternative Direct Link deployments

You can also establish diverse Connect deployments with IBM Cloud Direct Link, as shown in Figure 1.

![Diverse Connect](images/connect_alt_2.png "Diverse Connect"){: caption="A diverse IBM Cloud Direct Link Connect deployment to enable redundancy via Customer BGP schema" caption-side="bottom"}

## Using Connect along with other clouds
{: #using-exchange-and-connect-in-conjunction-with-other-clouds}

Some customers want to use Direct Link Connect along with other cloud providers, such as AWS, Azure, or Google Cloud. The following schematic shows an overview of how to establish this type of connection with a telco (service provider).

![Other Clouds Connect](images/connect_alt_3.png "Other Clouds Connect"){: caption="Using Direct Link Connect in conjunction with other clouds. Displays a single Direct Link, not a diverse deployment." caption-side="bottom"}
