---

copyright:
  years: 2021, 2022
lastupdated: "2022-10-21"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# How do I troubleshoot a Direct Link Dedicated connection during activation?  
{: #troubleshoot-level-1}
{: troubleshoot}
{: support}

I'm experiencing issues with the activation of my Dedicated connection. What should I do?
{: shortdesc}

The Direct Link Dedicated connection cannot establish end-to-end connectivity because the physical link is down.
{: tsSymptoms}

Possible causes include:
{: tsCauses}

* The single-mode fiber cable between the patch panel and edge device (router or switch) was not installed.
* An incorrect optic was used.
* There is a faulty cable, optic, or port along the path.
* The Site Provider installed the cross-connect in the wrong patch panel or ports.
* The port on the edge device is not up.
* The fiber's (RX/TX) strands are not aligned.

Follow these steps to troubleshoot Layer 1 (physical) issues:
{: tsResolve}

1. Compare the IBM Connecting Facility Assignment (CFA) details in the Letter of Authorization (LOA) to the cross-connect completion notice provided by the facility. Verify that the CFA details matches the cross-connect completion notice.

    Contact the facility owner if the cross-connect completion notice does not match up with the LOA/CFA.
    {: note}

    For an example of a cross-connect completion notice, see [Completion notice example](/docs/dl?topic=dl-completion-notice-example).

1. Verify that your router, or the network provider's router, is powered on and that the ports are up.
1. Ensure that device patching is complete. The single-mode fiber cable must be installed between the device to the patch panel.
1. Ensure that the device is using the correct optic.

    For 1G connections, use 1G optic; for connections greater than 1G, use a 10G optic. (1310nm optic - 1G=1000BASE-LX / 10G=10GBASE-LR)

1. Check the light levels from the Meet Me Room (MMR) to make sure that you're sending light to IBM and receiving light from IBM.
1. Try rolling the fiber by flipping TX/RX strands. Roll only one end, not both.
1. Make sure that the edge device port is set to auto-negotiate. If auto-negotiate does not work, then remove auto-negotiation by forcing the speed duplex settings.
1. Shut/no shut or disable/enable the interface if the port does not come up.

If these steps do not resolve the Direct Link Dedicated physical issue, contact the Advanced Customer Support (ACS) networking team and provide the gateway ID that is experiencing issues.
