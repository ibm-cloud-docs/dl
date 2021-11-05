---

copyright:
  years: 2020
lastupdated: "2020-05-15"

keywords:  

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
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}


# Deleting a {{site.data.keyword.dl_short}} gateway and its attached connections
{: #delete-direct-link-gateway}
{: help}
{: support}

You can delete a gateway either before or after the gateway moves to the **Provisioned** state. However, you cannot delete a gateway during the **In review** and some **in progress** states.
{: shortdesc}

To delete a gateway from the {{site.data.keyword.dl_short}} table, highlight the row of the gateway that you want to delete, then click **Delete** from the Overflow ![Overflow menu](images/overflow.png) menu. Alternatively, you can click **Actions > Delete** on a gateway's details page. Click **Delete** again to confirm the deletion.

If any virtual connections are attached to the gateway, you must detach them before you delete the gateway. To detach a virtual connection, click Delete ![Delete icon](images/garbage_icon.png) next to the connection entry on the gateway's details page. Then, click **Delete** to confirm.
{: important}
