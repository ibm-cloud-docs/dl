---

copyright:
  years: 2023
lastupdated: "2023-02-28"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# About route filtering
{: #filter-routes}

You can configure both import and export filters for a direct link.

* _Import route filters_ apply to on-premises routes that are learned by the direct link and advertised to the gateway's virtual connections. If a route is denied by an import filter, it is not added to the direct link's routing table.

* _Export route filters_ apply to the virtual connection routes learned by the direct link. These filters determine which routes get advertised to the on-premises network. If a route is denied by an export filter, it is included in the direct link's routing table, but is not advertised to the customer edge router (CER).

You can apply multiple filters of either direction to a direct link. You must first create the filters, then order them within the import or export route filter list. The decision to permit or deny a given route is determined by the first matching filter in the filter list. If no filter is matched, the default filter of the direction is applied.

Route filter configurations do not act as a firewall. Route filters affect only the subnets that are learned by the on-premises network. Route filters don't affect the addresses within the subnet after it's learned.
{: note}

Route filters include a prefix (an address and mask length), an optional minimum matching length (GE, greater than or equal to), and a maximum matching length (LE, less than or equal to). Combined, these values comprise the prefix match specifications of the route filter and determine if the filter will apply to a given route.

## Related links
{: #route-filtering-related-links}

* [Configuring route filters](/docs/dl?topic=dl-configure-route-filters)
* [Route filtering examples](/docs/dl?topic=dl-route-filtering-examples)
* [Filtering routes using Transit Gateway prefix filtering](/docs/dl?topic=dl-prefix-filtering)
