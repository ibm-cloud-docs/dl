---

copyright:
  years: 2021, 2026
lastupdated: "2026-05-18"

keywords: direct link

subcollection: dl
---

{{site.data.keyword.attribute-definition-list}}

# Updating the network connection type
{: #virtual-connection-types}

By default, your direct link is configured to create a direct, private connection between your on-premises network and IBM Cloud deployment. Optionally, you can choose to create
one or more network connections, either a classic infrastructure or VPC connection. You can also choose to connect your direct link to a transit gateway.

   You can choose the network connection type when creating a direct link, or after your direct link is provisioned.


To change the network connection type of a direct link, follow these steps:

1. Log in to your [{{site.data.keyword.cloud_notm}}](/login){: external} account.
1. Select the **Navigation menu** ![Menu icon](../icons/icon_hamburger.svg), then click **Infrastructure** ![VPC icon](../../icons/vpc.svg) > **Network** > **Direct link**.
1. Click **Direct Link** in the navigation pane.
1. Click the name of the direct link that you want to change the connection type for.
1. Expand the **Actions** menu in the upper right of the page, then click **Edit gateway**.
1. In the Edit configuration pane, scroll to the Connections section and update the connection type.

   To switch the type of virtual connection, you must first remove all virtual connections.
   {: important}

1. Click **Submit** for your changes to take effect.

The **Virtual connection type** is shown on the direct link's details page.
