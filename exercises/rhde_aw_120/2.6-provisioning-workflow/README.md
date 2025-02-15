# Workshop Exercise 2.1 - Creating a Provisioning Workflow

## Table of Contents

* [Objective](#objective)
* [Stem]
* [Step 1 - Adding Credentials to the Existing Job Template](#step-1---adding-credentials-to-the-existing-job-template)
* [Step 2 - Creating a Workflow](#step-2---creating-a-workflow)
* [Step 3 - Adding Workflow Nodes](#step-3---adding-workflow-nodes)
* [Solutions](#solutions)

## Objective

In this exercise, we're going to build a workflow that will fully deploy our edge devices. We want to take several steps automatically when the devices boot and call home, so a workflow makes perfect sense.

The basic idea of a workflow is to link multiple Job Templates together. They may or may not share inventory, playbooks or even permissions. The links can be conditional:

* if job template A succeeds, job template B is automatically executed afterwards
* but in case of failure, job template C will be run.

And the workflows are not even limited to Job Templates, but can also include project or inventory updates.

This enables new applications for Ansible automation controller: different Job Templates can build upon each other.

### Step 1 - Adding Credentials to the Existing Job Template

A job template has been created by the provisioner with an example playbook that tests connectivity to devices. This job template can be found on the **Templates** page under **Resources**.

Click on the job template name, then select **Edit** at the bottom of the page. Click the mangnifying glass icon next to **Credentials**. In the **Select Credentials** box, ensure **Selected Category** is set to **Machine**, and then select the **Device Credentials** created earler in [exercise 2.2](../2.2-kickstart-creds/). This will allow this job template to authenticate to your edge devices as they're provisioned.

### Step 2 - Creating a Workflow

Under **Resources**, select the **Templates** page. Once here, click **Add** > **Add workflow template**. Fill in the form with the following information:

<table>
  <tr>
    <th>Parameter</th>
    <th>Value</th>
  </tr>
  <tr>
    <td>Name</td>
    <td>Provision Edge Device</td>
  </tr>
  <tr>
    <td>Organization</td>
    <td>(Your_Student_Organization)</td>
  </tr>
  <tr>
    <td>Inventory</td>
    <td>Edge Systems</td>
  </tr>
  <tr>
    <td>Options</td>
    <td><ul><li>✓ Limit: Prompt on launch</li><li>✓ Enable Concurrent Jobs</li></ul></td>
  </tr>
</table>

Click **Save**

### Step 3 - Adding Workflow Nodes

After saving the workflow, you'll be presented with the workflow visualizer. Click the **Start** button to begin adding nodes.

We're going to add three nodes to our workflow to begin with:
1. Sync our code repo
2. Run the **Test Device Connectivity** job template
3. Run the **Initial Device Configuration** job template

These nodes should be connected via an **On-Success** connection in the workflow.

Once you've added the three nodes to the workflow, click the **Save** button in the top right corner.

### Solutions

#### Step 1:

![Test Connectivity Credentials](../images/test-connectivity-credentials.png)

#### Step 2:

![Workflow Inputs](../images/workflow-inputs.png)

#### Step 3:

##### Sync Code Node:

![Sync Code Node](../images/sync-code-node.png)

##### Test Device Connectivity Node:

![Test Connectivity Node](../images/test-connectivity-node.png)

##### Initial Device Configuration Node:

![Initial Device Configuration Node](../images/initial-device-config-workflow-node.png)

##### Finished Workflow:

![Finished Workflow](../images/initial-workflow-nodes.png)

---
**Navigation**

[Previous Exercise](../1.7-build-iso) | [Next Exercise](../3.1-boot-edge-device)

[Click here to return to the Workshop Homepage](../README.md)