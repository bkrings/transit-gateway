---

copyright:
  years: 2020, 2021
lastupdated: "2021-03-25"

keywords: editing, managing, manage, edit, add, connection

subcollection: transit-gateway

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}
{:external: target="_blank" .external}
{:term: .term}

# Managing transit gateways
{: #edit-gateway}

You can add, edit, or delete connections and edit your gateways from your {{site.data.keyword.tg_full}} using the {{site.data.keyword.cloud_notm}} console.
{: shortdesc}

## Adding a connection
{: #adding-connections}

To add a connection to a transit gateway, follow these steps:
1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://cloud.ibm.com){:external} and log in to your account.
1. Select the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) from the upper left, then click **Interconnectivity**.
1. Click **Transit Gateway** from the left navigation pane.
1. Click the name of the transit gateway where you want to add a connection.

  If you are in the expanded view, click **View details**.
  {: tip}

1. Click **Add connection**.

   You can now choose and configure the specific network connections that you want to add to your transit gateway.

   ![Add connections](images/addConnection.png "Adding connections")

## Adding a cross-account connection
{: #adding-cross-account-connections}

You can request connections to networks in other {{site.data.keyword.cloud_notm}} accounts.

  Only 10 pending requests are allowed per gateway. To create more requests, you can cancel the pending connection request, or wait for it to be approved. Connection requests expire if not approved within 72 hours.
  {: tip}

  Be aware that after you connect a transit gateway to a network in another account, all resources connected to that transit gateway are accessible from the other network. Make sure that this is a trusted account. Use of [security controls](/docs/vpc?topic=vpc-security-in-your-vpc), such as ACLs, security groups, or other network services to control traffic flow are highly recommended.
  {: important}

To connect networks owned by different accounts, follow these steps:

1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://cloud.ibm.com){:external} and log in to your account.
1. Select the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) from the upper left, then click **Interconnectivity**.
1. Click **Transit Gateway** from the left navigation pane.
1. Click the name of the transit gateway where you want to add a connection and click **Add connection**.
1. In the Add connection pane, select **Request connection to a network in another account**.
1. Type the VPC CRN of the cross-account network, or in the case of classic infrastucture, enter the IBM Cloud account ID that you want to connect to.

  To get the CRN of a VPC, from the {{site.data.keyword.cloud_notm}} console, select the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) from the upper left, and then click **Resource list**. Expand **VPC Infrastructure** to list your VPCs. Select a VPC and click **Status** to view its details. Copy the CRN and paste it into the Add connection pane.

  To get the IBM Cloud account ID, from the {{site.data.keyword.cloud_notm}} console, select **Manage > Account** and choose **Account Settings**. Your account ID shows in the **Account** section of the **Account settings** page.  

1. Type the name of the network connection, then click **Add**. The first screen capture shows adding a VPC connection, the second screen shows adding a classic infrastructure connection.

   ![Add VPC cross account connection](images/addCrossAcctConnection.png "Adding cross-account connection - VPC")

   ![Add classic infrastructure cross-account connection](images/addCrossAcctClassic.png "Adding cross-account connection - Classic infrastructure")

   The network connection now shows the **Pending** approval status in the gateway owner's account.

   The network owner's account then receives a notification of the request. If the network owner rejects the cross-account connection, no connectivity is established and the connection shows a status of **Rejected**. You can delete this connection at this point. If the cross-account connection is not explicitly approved, it expires after 72 hours.

   Connection requests can be resubmitted if they expire or are rejected.
   {: note}

1. A user with the [necessary IAM permissions](/docs/transit-gateway?topic=transit-gateway-iam) in the network owner's account can see the gateway and the details of all other connections attached to it in **View only** mode. From the network owner's account, go to the Transit Gateway page and click the gateway name in the table.
1. In the Connections section, see **Action required** to view the incoming network connection request. A user with the [necessary additional IAM permissions](/docs/transit-gateway?topic=transit-gateway-iam) can then click **Approve** to approve the request.

  After the network owner's account ensures that the connection request is from a legitimate source and approves it, the system establishes routes to and from all other networks connected to the same transit gateway. Use of [network ACLs and/or security groups](/docs/vpc?topic=vpc-security-in-your-vpc#security-in-your-vpc) within networks that are accessible across accounts are highly recommended to control the network traffic flows. You can unilaterally detach cross-account connections by either account through users who have the appropriate permissions.
  {: important}

  ![Approve cross-account connection](images/approveCrossAcctConnection.png "Approve cross-account connection")

  Click **Approve** to confirm.

  ![Confirm cross account connection](images/confirmCrossAcctConnection.png "Confirm cross-account connection")

  The status of the network connection indicates **Attaching**.

1. When you change back to the original account, the status of the connection changes to **Attached**, indicating that the network request was approved.

  ![Attached cross-account connection](images/attachedCrossAcctConnection.png "Attached cross-account connection")

  The gateway owner's account (or the network owner's account) can delete the connection. If the network owner deletes the connection, the gateway owner sees the connection status as **Detached**.
  {: note}

## Editing a connection
{: #editing-connections}

To edit a connection to a transit gateway, follow these steps:

1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://cloud.ibm.com){:external} and log in to your account.
1. Select the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) from the upper left, then click **Interconnectivity**.
1. Click **Transit Gateway** from the left navigation pane.
1. Click the name of the transit gateway where you want to edit a connection.

  If you are in the expanded view, click **View details**.
  {: tip}

1. From the Connections page, click the Options menu icon ![Options icon](../../icons/actions-icon-vertical.svg) next to the connection that you want to edit and select **Edit**.

   From here, you can change the name of the selected network connection.

   ![Edit connections](images/7-editingGlobaltoLocalTG.png "Editing connections")

## Deleting a connection
{: #deleting-connections}

To delete a connection from a transit gateway, follow these steps:

1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://cloud.ibm.com){:external} and log in to your account.
1. Select the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) from the upper left, then click **Interconnectivity**.
1. Click **Transit Gateway** from the left navigation pane.
1. Click the name of the transit gateway where you want to delete a connection.

  If you are in the expanded view, click **View details**.
  {: tip}

1. From the Connections page, click the Options menu icon ![Options icon](../../icons/actions-icon-vertical.svg) next to the connection that you want to delete and select **Delete**.

   ![Delete connections with the Options menu](images/deleteConnection.png "Delete connections with the Options menu")

## Changing your configuration
{: #change-configuration}

To change your transit gateway configuration, follow these steps:

1. From your browser, open the [{{site.data.keyword.cloud_notm}} console](https://cloud.ibm.com){:external} and log in to your account.
1. Select the Menu icon ![Menu icon](../../icons/icon_hamburger.svg) from the upper left, then click **Interconnectivity**.
1. Click **Transit Gateway** from the left navigation pane.
1. Click the name of the transit gateway you want to edit.

  If you are in the expanded view, click **View details**.
  {: tip}

1. Click **Edit**.

   From here, you can change the gateway's name and its routing type (Local or Global).

   To change a transit gateway's routing type from Global to Local, you must delete any connections that are not local to the transit gateway's location.
{: tip}

   When changing from Local to Global routing for a given transit gateway, you are charged for all associated connection traffic.
{: important}

   ![Editing your configuration](images/editConnection.png "Editing your configuration")
