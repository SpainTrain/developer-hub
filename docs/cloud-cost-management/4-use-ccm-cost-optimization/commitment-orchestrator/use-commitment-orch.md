---
title: Set up Commitment Orchestrator
description: Optimize the utilization of Amazon EC2 Reserved Instances (RIs) by setting up Harness Commitment Orchestrator. 
sidebar_position: 3
---  

:::note
Currently, this feature is behind the feature flag **CCM_COMM_SETUP**. Contact [Harness Support](mailto:support@harness.io) to enable the feature.
:::

This topic explains how to optimize the utilization of Amazon EC2 Reserved Instances (RIs) by setting up Harness Commitment Orchestrator. 


## Prerequisites

Ensure that you meet the following prerequisites to set up Commitment Orchestrator:

* Add the master payer account of AWS in Harness with CUR configured. For more information, go to [Cost and Usage Report](https://docs.aws.amazon.com/cur/latest/userguide/cur-create.html).
* If you want to view the commitment utilization data and the potential cost savings, you need to enable the permissions as displayed in the following screenshot: 
  
    <docimage path={require('./static/commitment-visibility-permissions.png')} width="50%" height="50%" title="Click to view full size image" />

 If you want to set up commitment orchestrator and enable automated actions, you must add the set of roles on the master account to enable Harness to perform certain actions as displayed in the following screenshot:

  <docimage path={require('./static/commitment-setup-permissions.png')} width="50%" height="50%" title="Click to view full size image" />

 For more information about the permissions that need to be added, go to [Set up CCM for AWS](../../get-started/onboarding-guide/set-up-cost-visibility-for-aws.md#commitment-orchestrator).

  
* Enable Cost Explorer to show data linked to child accounts. For more information, go to [Granting Cost Explorer Access](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-access.html#grant-ce-access).


## Set up Commitment Orchestrator

Perform the following tasks to configure commitment orchestrator in your environment: 

1. In the Harness application, go to **Cloud Costs**.
2. Select **Commitment Orchestrator**.
3. Select **Setup**.
4. The **Setup Commitment Orchestrator** wizard guides you through the following steps required to set up Commitment Orchestrator.
    1. On the **Coverage Percentage and SP/RI split** page, do the following
    
    - **Specify Coverage Percentage**
    
     Specify the percentage of compute spend that you want to be covered by Savings Plans and RIs. For example, if you choose to cover 70% of the total spend by Savings Plans and RIs, the remaining 30% would be handled by On-Demand and Spot (if applicable) instances. Note that this setup applies to your entire AWS account including child accounts. 
    - **Specify the split between Savings Plans and RIs**

      Specify the desired distribution between Convertible Reserved Instances (RIs) and Compute Savings Plans to adequately cover your entire compute expenditure.  

    This Savings Plan covers your compute costs for a duration of one year without any upfront payment. For more information about the different Savings Plans payment strategies, go to [What are Savings Plans?](https://docs.aws.amazon.com/savingsplans/latest/userguide/what-is-savings-plans.html)

    <docimage path={require('./static/setup-1.png')} width="50%" height="50%" title="Click to view full size image" />

   2. Select **Continue**.

   3. On the **Exclude Instance Types** page, all the instance types currently in use are displayed in the table. By default, all the rows are selected and all of these instance types in the specified region are considered for RI conversions and purchases. However, you can deselect to exclude the instance types that you might not use.
   
    You can use the **Instance family** filter to view Instance types of a particular Instance family and the **Region** filter to view all Instance types available in that region. 

    <docimage path={require('./static/setup-2.png')} width="50%" height="50%" title="Click to view full size image" />

   4. Select **Continue**.
   5. Carefully review the automated actions displayed on the **Review** page. You can also view the **Current Compute Spend**, **Target Compute Spend**, and **Projected Potential Savings** based on the setup. 

   The following automated actions will be taken to optimize utilization:

   - The Commitment Orchestrator continuously looks for opportunities to acquire or convert Reserved Instances (RIs). Staggered daily purchases are made rather than buying in bulk.
   - Purchase Savings Plans.
   
    You can find a record of all its actions in the **Log History** on the summary page.
  
  6. Select the checkbox to provide consent to perform the automated actions on your behalf. 
  7. Select **Confirm**.

    <docimage path={require('./static/setup-3.png')} width="50%" height="50%" title="Click to view full size image" />


You have successfully set up the Commitment Orchestrator. 