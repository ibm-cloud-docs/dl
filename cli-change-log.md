---

copyright:
  years: 2022, 2025
lastupdated: "2025-07-21"

keywords: direct link cli change log

subcollection: dl

content-type: release-note

---

{{site.data.keyword.attribute-definition-list}}

# Direct Link CLI change log
{: #direct-link-cli-change-log}

Learn about recent changes, improvements, and updates for the IBM Cloud Direct Link CLI plug-in (`ibmcloud dl`). Changes to existing CLI versions are compatible with existing client applications.
{: shortdesc}

To learn about general updates and improvements to Direct Link offerings, see the [Release notes for Direct Link](/docs/dl?topic=dl-direct-link-release-notes).
{: note}

## 17 June 2025
{: #dl-jun1725}
{: release-note}

MACsec support for Direct Link Dedicated

:    New commands:

   * [View details of a CAK by ID](/docs/dl?topic=dl-dl-cli#cak)
   * [List all CAKs](/docs/dl?topic=dl-dl-cli#caks)
   * [Create a CAK](/docs/dl?topic=dl-dl-cli#cak-create)
   * [Delete a CAK](/docs/dl?topic=dl-dl-cli#cak-delete)
   * [Update a CAK](/docs/dl?topic=dl-dl-cli#cak-update)
   * [View details of a MACsec configuration](/docs/dl?topic=dl-dl-cli#macsec)
   * [Set the MACsec configuration](/docs/dl?topic=dl-dl-cli#macsec-set)
   * [Unset the MACsec configuration](/docs/dl?topic=dl-dl-cli#macsec-unset)
   * [Update the MACsec configuration](/docs/dl?topic=dl-dl-cli#macsec-update)

## 07 March 2024
{: #dl-mar0724}
{: release-note}

VLAN tagging support for Direct Link Dedicated

:    Updated commands:

   * [Create a dedicated gateway](/docs/dl?topic=dl-dl-cli#create-dedicated-gateway)
   * [Update a specific gateway](/docs/dl?topic=dl-dl-cli#update-gateway)

## 06 July 2023
{: #dl-jul0623}
{: release-note}

Route report enhancements
:    Shows new route report fields for advertised routes and AS path.

## 16 March 2023
{: #dl-mar1623}
{: release-note}

BGP route filter support

:    New commands:

     Export route filters

   * [View details of an export route filter by ID](/docs/dl?topic=dl-dl-cli#export-route-filter) - `export-route-filter`, `erf`
   * [List all export route filters](/docs/dl?topic=dl-dl-cli#export-route-filters) - `export-route-filters`, `erfs`
   * [Create an export route filter](/docs/dl?topic=dl-dl-cli#export-route-filter-create) - `export-route-filter-create`, `erfc`
   * [Delete an export route filter](/docs/dl?topic=dl-dl-cli#export-route-filter-delete) - `export-route-filter-delete`, `erfd`
   * [Replace all export route filters](/docs/dl?topic=dl-dl-cli#export-route-filter-replace) - `export-route-filter-replace`, `erfr`
   * [Update an export route filter](/docs/dl?topic=dl-dl-cli#export-route-filter-update) - `export-route-filter-update`, `erfu`

    Import route filters

   * [View details of an import route filter by ID](/docs/dl?topic=dl-dl-cli#import-route-filter) - `import-route-filter`, `irf`
   * [List all export route filters](/docs/dl?topic=dl-dl-cli#import-route-filters) - `import-route-filters`, `irfs`
   * [Create an export route filter](/docs/dl?topic=dl-dl-cli#import-route-filter-create) - `import-route-filter-create`, `irfc`
   * [Delete an export route filter](/docs/dl?topic=dl-dl-cli#import-route-filter-delete) - `import-route-filter-delete`, `irfd`
   * [Replace all export route filters](/docs/dl?topic=dl-dl-cli#import-route-filter-replace) - `import-route-filter-replace`, `irfr`
   * [Update an export route filter](/docs/dl?topic=dl-dl-cli#import-route-filter-update) - `import-route-filter-update`, `irfu`

## 21 September 2022
{: #dl-sep1222}
{: release-note}

BGP AS prepend support
:    Support AS prepend information as part of the `--file` option.

   * [Create a Connect gateway](/docs/dl?topic=dl-dl-cli#create-connect-gateway) - `connect-gateway-create`, `conn-gwc`
   * [Create a Dedicated gateway](/docs/dl?topic=dl-dl-cli#create-dedicated-gateway) - `dedicated-gateway-create`, `ded-gwc`
   * [Approve a gateway change request](/docs/dl?topic=dl-dl-cli#gateway-change-approve-cmd) - `gateway-change-approve`, `gwca`

Route report support
:    New commands:

   * [View details of a route report](/docs/dl?topic=dl-dl-cli#route-report-view) - `route-report`, `rr`
   * [Create a route report](/docs/dl?topic=dl-dl-cli#route-report-create-view) - `route-report-create`, `rrc`
   * [Delete a route report](/docs/dl?topic=dl-dl-cli#route-report-delete-view) - `route-report-delete`, `rrd`
   * [List all route reports](/docs/dl?topic=dl-dl-cli#route-report-list-view) - `route-reports`, `rrs`
