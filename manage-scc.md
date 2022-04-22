---
copyright:
  years: 2020, 2022
lastupdated: "2022-03-21"

keywords: security, compliance, direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Managing security and compliance with IBM Cloud Direct Link
{: #manage-security-compliance}

{{site.data.keyword.dl_full}} is integrated with the {{site.data.keyword.compliance_short}} to help you manage security and compliance for your organization.
{: shortdesc}

With the {{site.data.keyword.compliance_short}}, you can: 

* Monitor for controls and goals that pertain to {{site.data.keyword.dl_full}}.
* Define rules for {{site.data.keyword.dl_full}} that can help to standardize resource configuration.

## Monitoring security and compliance posture with {{site.data.keyword.dl_full_notm}}
{: #monitor-directlink}

As a security or compliance focal, you can use the {{site.data.keyword.dl_full_notm}} [goals](x2117978){: term} to help ensure that your organization is adhering to the external and internal standards for your industry. By using the {{site.data.keyword.compliance_short}} to validate the resource configurations in your account against a [profile](x2034950){: term}, you can identity potential issues as they arise.

All of the goals for {{site.data.keyword.dl_full_notm}} are added to the {{site.data.keyword.cloud_notm}} Best Practices Controls 1.0 profile, but can also be mapped to other profiles.
{: note}

To start monitoring your resources, check out [Getting started with {{site.data.keyword.compliance_short}}](/docs/security-compliance?topic-security-compliance-getting-started).

### Available goals for {{site.data.keyword.dl_full_notm}}
{: #available-goals}

* Check whether Direct Link (2.0) allows no cross account connection requests at the account level
* Check whether Direct Link (2.0) allows no cross account connection approvals at the account level

## Governing {{site.data.keyword.dl_full_notm}} resource configuration
{: #govern-directlink}

As a security or compliance focal, you can use the {{site.data.keyword.compliance_short}} to define configuration rules for the instances of {{site.data.keyword.dl_full}} that you create.

[Config rules](#x3084914){: term} are used to enforce the configuration standards that you want to implement across your accounts. To learn more about the data that you can use to create a rule for {{site.data.keyword.dl_full}}, review the following table.

| Resource kind | Property | Operator | Value | Description |
|---------------|----------|---------------|-------|-------------|
| *service* | *cross_account_connection_approved* | *is_false* | - | Indicates whether an incoming cross account connection request was approved. |
{: caption="Table 1. Rule properties for {{site.data.keyword.dl_full}}" caption-side="bottom"}

To learn more about config rules, check out [What is a config rule?](/docs/security-compliance?topic=security-compliance-what-is-governance)
