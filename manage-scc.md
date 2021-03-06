---
copyright:
  years: 2020, 2021
lastupdated: "2021-03-26"

keywords: security, compliance

subcollection: dl

---

{:external: target="_blank" .external}
{:note: .note}
{:term: .term}
{:shortdesc: .shortdesc}
{:table: .aria-labeledby="caption"}

# Managing security and compliance with IBM Cloud Direct Link
{: #manage-security-compliance}

{{site.data.keyword.dl_full}} is integrated with the {{site.data.keyword.compliance_short}} to help you manage security and compliance for your organization.
{: shortdesc}

<!--Add the following sections as your service onboards to the Security and Compliance Center. You might have only monitoring or you might also have configuration enforcement. Also, if you only have one of the options, be sure to remove the bulleted list and write the following section as a sentence.-->

With the {{site.data.keyword.compliance_short}}, you can: 
* Monitor for controls and goals that pertain to {{site.data.keyword.dl_full}}.
* Define rules for {{site.data.keyword.dl_full}} that can help to standardize resource configuration.

## Monitoring security and compliance posture with {{site.data.keyword.dl_full_notm}}
{: #monitor-directlink}

As a security or compliance focal, you can use the {{site.data.keyword.dl_full_notm}} [goals](x2117978){: term} to help ensure that your organization is adhering to the external and internal standards for your industry. By using the {{site.data.keyword.compliance_short}} to validate the resource configurations in your account against a [profile](x2034950){: term}, you can identity potential issues as they arise.

All of the goals for {{site.data.keyword.dl_full_notm}} are added to the {{site.data.keyword.cloud_notm}} Best Practices Controls 1.0 profile, but can also be mapped to other profiles.
{: note}

To start monitoring your resources, check out [Getting started with {{site.data.keyword.compliance_short}}](https://cloud.ibm.com/docs/security-compliance?topic-security-compliance-getting-started).

### Available goals for {{site.data.keyword.dl_full_notm}}
{: #available-goals}

* *Ensure at the account-level that no cross-account connection approvals can be done via {{site.data.keyword.dl_full}}*
* *Ensure at the account-level that no cross-account connection requests can be made via {{site.data.keyword.dl_full}}*

## Governing {{site.data.keyword.dl_full_notm}} resource configuration
{: #govern-directlink}

As a security or compliance focal, you can use the {{site.data.keyword.compliance_short}} to define configuration rules for the instances of {{site.data.keyword.dl_full}} that you create.

[Config rules](#x3084914){: term} are used to enforce the configuration standards that you want to implement across your accounts. To learn more about the data that you can use to create a rule for {{site.data.keyword.dl_full}}, review the following table.

| Resource kind | Property | Operator | Value | Description |
|---------------|----------|---------------|-------|-------------|
| *service* | *cross_account_connection_approved* | *is_false* | - | *Indicates whether an incoming cross account connection request was approved. |
{: caption="Table 1. Rule properties for {{site.data.keyword.dl_full}}" caption-side="top"}

To learn more about config rules, see [What is a config rule?](/docs/security-compliance?topic=security-compliance-what-is-rule).
