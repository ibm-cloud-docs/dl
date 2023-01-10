---

copyright:
  years: 2022
lastupdated: "2022-09-21"

keywords: direct link api change log

subcollection: dl

content-type: release-note

---

{{site.data.keyword.attribute-definition-list}}

# Direct Link API change log
{: #direct-link-api-changelog}

Check back regularly to see what's new with {{site.data.keyword.cloud}} Direct Link API.
{: shortdesc}

## 21 September 2022
{: #dl-sept2122}

Route report support
:   New commands

   * List route reports - `GET /gateways/{gateway_id}/route_reports`
   * Create a route report - `POST /gateways/{gateway_id}/route_reports`
   * Delete route report - `DELETE /gateways/{gateway_id}/route_reports/{id}`
   * Get a route report - `GET /gateways/{gateway_id}/route_reports/{id}`
   
BGP AS prepend support
:   Changed commands

   * Add AS prepend support during create gateway - `POST /gateways`
   * Add AS prepend support during create gateway approve - `POST gateways/{id}/actions`

## 01 April 2022
{: #dl-april0122}
{: release-note}

Reduced unmetered plan pricing for Direct Link Connect
:   IBM is pleased to announce _a significant reduction in unmetered pricing_ for IBM Cloud Direct Link Connect and Direct Link Dedicated. Note that Direct Link also offers a metered pricing plan, allowing you to switch between metered and unmetered pricing plans to suit your bandwidth usage needs. For more information, see [Pricing for IBM Cloud Direct Link](/docs/dl?topic=dl-pricing-for-ibm-cloud-dl).

