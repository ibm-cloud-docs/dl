---

copyright:
  years: 2023, 2024
lastupdated: "2024-06-19"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Route filtering examples
{: #route-filtering-examples}

## How filters are matched
{: #matching-filter}

To describe how filters are matched, consider the following gateway setup:

* `default_import_route_filter: permit`
* `import_route_filters`
   * 1 - `permit 10.10.0.0/19`
   * 2 - `deny 10.10.0.0/16 ge 18 le 30`
   * 3 - `deny 120.120.154.0/24`
* `default_export_route_filter: deny`
* `export_route_filters`
   * `permit 10.10.0.0/18`

### Importing routes
{: #importing-routes-example}

For this example, routes from the customer on-premises network pass through the `import_route_filters` to determine whether the direct link learns them or not. Let's first understand the route filters:

```sh
Route filter 1
Action: permit
Address: 10.10.0.0
Mask length: 19
Minimum matching length (ge): 19
Maximum matching length (le): 19

Route filter 2
Action: deny
Address 10.10.0.0
Mask length: 16
Minimum matching length (ge): 18
Maximum matching length (le): 30

Route filter 3
Action: deny
Address 120.120.154.0
Mask length: 24
Minimum matching length (ge): 24
Maximum matching length (le): 24
```
{: screen}

Consider an on-premises network connected to a direct link with the following routes:

* Route 1 - `10.10.0.0/16`
* Route 2 - `10.10.0.0/18`
* Route 3 - `10.10.0.0/19`
* Route 4 - `120.120.154.0/24`
* Route 5 - `10.10.128.0/18`

Only Route 1 - `10.10.0.0/16` and Route 3 - `10.10.0.0/19` would be learned by the direct link and advertised to attached virtual connections.

* Route 1 - `10.10.0.0/16` does not match with any import filter.
    * The route matches filter 2 by address and mask length, but the `ge` option changes the prefix match specification, excluding route 1's mask of `/16`.
    * The default import filter determines how this route is handled, which is `permit`.
* Route 2 - `10.10.0.0/18` only matches with import filter 2.
    * The `ge` and `le` options of filter 2 alter the prefix match specifications to include route 2 with a mask of `/18`.
    * Filter 2's action is `deny`, so route 2 will not be learned.
* Route 3 - `10.10.0.0/19` matches with import filter 1 and 2.
    * The route matches filter 1 by address and mask length. Filter 1 has no `ge` or `le` values, so only the exact mask length would match.
    * The `ge` and `le` options of filter 2 alter the prefix match specifications to include route 2 with a mask of `/19`.
    * Filter 1 is before filter 2 in the list giving higher precedence. That filter action is set to `permit`, so the route goes through and is learned.
* Route 4 - `120.120.154.0/24` matches filter 3 exactly.
    * Filter 3's action is set to `deny`, so route 4 will not be learned.
* Route 5 matches rule 2 (`deny 10.10.0.0/16 ge 18 le 30`), therefore route 5 is denied. Moving the prefix into the subnet of `18` expands the address of `10.10.128.0/18`.

### Exporting routes
{: #exporting-routes-example}

For this example, direct link routes learned from any virtual connection would pass through the `export_route_filters` to determine whether the direct link advertises them to the customer's on-premises network.

Let's first understand the route filters.

```sh
Route filter 1
Action: permit
Address 10.10.0.0
Mask length: 18
Minimum matching length (ge): 18
Maximum matching length (le): 18
```
{: screen}

Consider a direct link with virtual connections with the following routes:

* Route 1 - `10.10.0.0/18`
* Route 2 - `10.10.0.0/19`

Only Route 1 - `10.10.0.0/18` would be advertised to the customer's on-premises network.

* Route 1 - `10.10.0.0/18` matches on export filter 1.
    * Filter 1's action is set to `permit`, so route 1 will be advertised.
* Route 2 - `10.10.0.0/19` does not match with any export filter.
    * The default export filter determines how this route is handled, which is `deny`.
    * In fact, besides route 1, any other route will be not advertised. No other route will match a filter in the `export` list.

## Advanced matching examples
{: #examples-matching-examples}

Rather than configuring multiple route filters for consecutive subnets, you can configure a filter with a summary route and qualifying maximum and minimum matching lengths that will match with the consecutive subnets.

### No minimum (GE) or maximum (LE) matching length values
{: #no-min-max-matching-length}

The route filter with prefix `192.168.64.0/18` will only match a single subnet `192.168.64.0/18`.

### Equal minimum (GE) and maximum (LE) matching length values
{: #equal-min-max-matching-length}

The route filter with prefix `192.168.0.0/16`, GE `18`, and LE `18` will match the following subnets:

* `192.168.0.0/18`
* `192.168.64.0/18`
* `192.168.128.0/18`
* `192.168.192.0/18`

### Unequal minimum (GE) and maximum (LE) matching length values
{: #unequal-min-max-matching-length}

The route filter with prefix `192.168.0.0/16`, GE `18`, and LE `19` will match the following subnets:

* `192.168.0.0/18`
* `192.168.64.0/18`
* `192.168.128.0/18`
* `192.168.192.0/18`
* `192.168.0.0/19`
* `192.168.32.0/19`
* `192.168.64.0/19`
* `192.168.96.0/19`
* `192.168.128.0/19`
* `192.168.160.0/19`
* `192.168.192.0/19`
* `192.168.224.0/19`

### Only minimum (GE) matching length specified
{: #only-min-matching-length}

The route filter with prefix `192.168.0.0/30`, GE `30` will match the following subnets (maximum matching length is considered `32`):

* `192.168.0.0/30`
* `192.168.0.0/31`
* `192.168.0.2/31`
* `192.168.0.0/32`
* `192.168.0.1/32`
* `192.168.0.2/32`
* `192.168.0.3/32`

### Only maximum (LE) matching length specified
{: #only-max-matching-length}

The route filter with prefix `192.168.0.0/16` and LE `19` will match the following subnets (minimum matching length is considered `16`):

* `192.168.0.0/16`
* `192.168.0.0/17`
* `192.168.128.0/17`
* `192.168.0.0/18`
* `192.168.64.0/18`
* `192.168.128.0/18`
* `192.168.192.0/18`
* `192.168.32.0/19`
* `192.168.64.0/19`
* `192.168.96.0/19`
* `192.168.128.0/19`
* `192.168.160.0/19`
* `192.168.192.0/19`
* `192.168.224.0/19`
