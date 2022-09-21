---

copyright:
  years: 2020
lastupdated: "2020-05-15"

keywords: direct link

subcollection: dl
---

{{site.data.keyword.attribute-definition-list}}

# Deleting a direct link and its attached connections
{: #delete-direct-link-gateway}
{: help}
{: support}

You can delete a direct link either before or after the gateway moves to the **Provisioned** state. However, you cannot delete a gateway during the **In review** and some **in progress** states.
{: shortdesc}

To delete a gateway from the {{site.data.keyword.dl_short}} table, highlight the row of the gateway that you want to delete, then click **Delete** from the Actions ![Actions menu](images/overflow.png) menu. Alternatively, you can click **Actions > Delete** on a gateway's details page. Click **Delete** again to confirm the deletion.

If any virtual connections are attached to the gateway, you must detach them before you delete the gateway. To detach a virtual connection, click Delete ![Delete icon](images/garbage_icon.png) next to the connection entry on the gateway's details page. Then, click **Delete** to confirm.
{: important}
