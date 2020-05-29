---

copyright:
  years: 2020
lastupdated: "2020-03-03"

keywords: public isolation for Direct Link, compute isolation for Direct Link, Direct Link architecture, workload isolation in Direct Link

subcollection: dl

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:table: .aria-labeledby="caption"}
{:tip: .tip}
{:important: .important}
{:note: .note}

# Learning about Direct Link architecture and workload isolation
{: #compute-isolation}

[GUIDANCE](/docs/writing?topic=writing-architecture-compute-isolation) 

This template is optional for services with differentiating isolation characteristics. Other services don’t need to provide this documentation as part of the end-user content.

_The short description should be a single, concise paragraph that contains one or two sentences and no more than 50 words. Summarize your offering's architecture and support for isolating one tenants' workload from another._

Review the following sample architecture for Direct Link, and learn more about different isolation levels so that you can choose the solution that best meets the requirements of the workloads that you want to run in the cloud.
{: shortdesc}

## Direct Link architecture
{: #architecture}

_Review the following example: https://cloud.ibm.com/docs/containers?topic=containers-service-arch. Review the System Architecture Guide: https://pages.github.ibm.com/CloudEngineering/system_architecture/services/multitenancy.html. Provide an arch overview diagram identifying what runs within the IBM Service Account and what runs in the customer's account._

## Direct Link workload isolation
{: #workload-isolation}

_Document how customer workloads are isolated from each other by plan. Do customer workloads run within the customer account?  Are customer workloads isolated within Kubernetes namespaces? Do customer workloads run on dedicated compute? Check out the example from Kubernetes: https://cloud.ibm.com/docs/containers?topic=containers-service-arch#worker-components_
