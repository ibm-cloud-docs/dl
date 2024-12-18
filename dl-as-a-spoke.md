---

copyright:
  years: 2021, 2024
lastupdated: "2024-12-18"

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
1. Click Menu ![Menu icon](images/menu_icon.png) on the upper left of the page, then click **Infrastructure** > **Network** > **Direct Link**.
1. Click **Direct Link** in the navigation pane.
1. Click the name of the direct link that you want to change the connection type for.
1. Expand the **Actions** menu in the upper right of the page, then click **Edit gateway**.
1. In the Edit configuration pane, scroll to the Connections section and update the connection type.

   To switch the type of virtual connection, you must first remove all virtual connections.
   {: important}

1. Click **Submit** for your changes to take effect.

If you selected **Transit Gateway** as your network connection type, you must use the same account to create a network connection to your direct link by using the [{{site.data.keyword.cloud_notm}} Transit Gateway console](/interconnectivity/transit){: external}. Keep in mind that classic routes are not blocked. For more information, see [Preparing for Direct Link changes to advertised service network routes](/docs/dl?topic=dl-notification-dl-tgw).
{: important}

The **Virtual connection type** is shown on the direct link's details page.
