---

copyright:
  years: 2019
lastupdated: "2019-12-15"

keywords: direct link, configure, connection

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

# Adding virtual connections to a Direct Link gateway
{: #add-virtual-connection}

You can add a virtual connection when you create a Direct Link gateway using the Network connections option. You can also add a virtual connection to the gateway after you create it. To do so, follow these steps:

1. On the gateway's details page, click **Add Connection +** to add a virtual connection to an existing gateway. You can create a new connection to the logged-in account, or request a connection to a network within another account.
2. Select a network connection and then select your region from the menu list.
3. Select the VPC network to attach to the gateway and enter a name for the connection.
4. Click **Add** to attach the virtual connection to the gateway.

After adding the virtual connection to the gateway, the VPC name displays under the virtual connections section on the gateway's details page.

You can add only one classic infrastructure virtual connection to a provisioned Direct Link connection; however, you can add multiple VPC virtual connections.
{: note}
