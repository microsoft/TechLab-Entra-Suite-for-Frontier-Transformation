@lab.Title

**Please enter your own Microsoft alias (without the @microsoft.com) in the field below before starting the lab**. This information is required to correctly associate your activity with your learner record and ensure your completion is accurately captured and reported. For data integrity and compliance reasons, learners may only enter their own alias.   After completing the lab, please allow up to 5 business days for all reporting systems to fully reflect your completion.

@lab.ActivityGroup(aliascapture)

===


## Survey

@lab.ActivityGroup(initialsurvey)

===


## Introduction

Microsoft Entra Suite is a Zero Trust user access solution that unifies identity governance, identity protection, identity verification, and network access security under a single Conditional Access policy engine. 

## Objectives

After completing this lab, you'll be able to:

- Automate user lifecycle and entitlements with lifecycle workflows, access packages, and risk-based Conditional Access.
- Replace VPN with per-app, identity-brokered access to on-premises applications using Global Secure Access Private Access.
- Configure just-in-time, time-bound access to sensitive resources with multi-stage approval and recurring access reviews.
- Apply network content filtering, MCP traffic discovery, and prompt injection protection to bring AI traffic - both human and agent - under enterprise identity policy.

## Duration

**Estimated time:** 4 hours

===

# Exercise 00: Set up your environment

## Scenario
You've just stepped into a new role supporting Zava's IoT business. Before you can do anything meaningful, your organization needs to establish a secure, identity-first foundation that allows your access to be governed, evaluated, and enforced consistently across devices and services.
This initial setup ensures that your identity, device, and authentication context can be trusted-forming the groundwork for every access decision that follows.
## Objectives
In this exercise, you'll:
- Activate Microsoft Entra Suite capabilities.
- Configure identity and licensing for your user account.
- Establish a compliant, Entra-joined device.
- Prepare your user context for policy enforcement.

## Duration
Estimated time: 15 minutes

===

>[!TIP]
>As you follow the instructions in this pane, you can select highlighted +++Type Text+++ to write it directly into the virtual machine.

## Task 01: Activate the Entra Suite trial
### Introduction
Modern identity security begins with a unified control plane. Microsoft Entra Suite consolidates identity governance, authentication, and network access into a single policy-driven system. This eliminates fragmented controls and allows security decisions to follow identity rather than location.
### Description
In this task, you activate the Entra Suite environment and establish administrative access. This enables all downstream capabilities-such as lifecycle workflows, Conditional Access, and identity-based network controls-to operate under a shared policy engine.
### Example scenario
You're Adele, and on your first day in this new role, your organization enables a unified identity platform. Instead of managing separate systems for access, networking, and security, everything is now governed through a single identity layer that will determine what you can access-and under what conditions.
### Success criteria
- Entra Suite is active and accessible
- Administrative access is established
- Identity services are ready for governance configuration
### Learning resources
- Microsoft Entra overview
- Zero Trust identity principles

---

1. Sign in to the @lab.VirtualMachine(Windows11).SelectLink VM with the following credentials:



	| Item     | Value                                                |
	|:---------|:---------|
	| Username | **@lab.VirtualMachine(Windows11).Username**       |
	| Password | **+++@lab.VirtualMachine(Windows11).Password+++** |

1. Open Microsoft Edge, then go to `admin.cloud.microsoft/?pid=2EBF8FFA-7DE1-4D14-9B15-238F5CA77671&mpid=CFQ7TTC0NZT8%2C0001&ru=signup#/Purchase/trial`.


1. Sign in with your lab credentials:



	| Item     | Value                                                |
	|:---------|:---------|
	| Username | `@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).AdministrativeUsername`       |
	| Password | `@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).AdministrativePassword`  |

	>[!alert] You'll need a personal mobile device to set up MFA on the account.

1. In the dialog for MFA, select **Set up now**.



	!IMAGE[ldz73e3p.png](../../media/ldz73e3p.png)

1. Follow the onscreen prompts to use the **Microsoft Authenticator** app to enable MFA.


1. Once added, select **Done**.


1. In the rightmost pane of the trial activation page, select **Try now**.



	!IMAGE[xdytkj7i.png](../../media/xdytkj7i.png)

1. Once activated, select **Go to Admin Home**.



	!IMAGE[94tk5gts.png](../../media/94tk5gts.png)

===

## Task 02: Add licenses
### Introduction
Licensing is what enables capabilities at the identity level. Without proper licensing, advanced governance, risk detection, and access enforcement features aren't available to users.
### Description
You assign Entra Suite licenses to both administrative and user identities. This ensures that your user account (Adele) can participate in automated lifecycle workflows, Conditional Access evaluation, and secure access scenarios later in the lab.
### Example scenario
You're Adele, and your access experience should reflect your role immediately. Behind the scenes, your organization assigns you the necessary licenses so your identity can be evaluated, governed, and protected according to Zero Trust principles.
### Success criteria
- Licenses assigned to required users
- Adele's account has Entra Suite capabilities enabled
- Identity is ready for governance and enforcement scenarios
### Learning resources
- Identity licensing concepts in Microsoft Entra

---

1. In the leftmost pane, go to **Billing** > **Licenses**.


1. Select **Microsoft Entra Suite**.


1. Above the table, select **Assign licenses**.



	!IMAGE[hhtvcr6x.png](../../media/hhtvcr6x.png)

1. In the flyout pane:


1. Search for and select the following accounts:



        - `@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).AdministrativeUsername`
        - `AdeleV@@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).TenantName`

		!IMAGE[3tsue9vs.png](../../media/3tsue9vs.png)

1. At the bottom of the pane, select **Assign licenses**.



		!IMAGE[zeelmwhv.png](../../media/zeelmwhv.png)

1. Close the flyout pane.



===

## Task 03: Set up end user account
### Introduction
A user identity is more than just credentials-it includes attributes, authentication methods, and policy context. These attributes drive automated decisions across governance and access enforcement systems.
### Description
You configure Adele's account and authentication setup. This prepares the identity for secure sign-in, multi-factor authentication, and policy evaluation across applications and services.
### Example scenario
You're Adele, signing in for the first time. Your identity is configured with strong authentication methods, ensuring that every access request you make can be validated with high assurance from the start.
### Success criteria
- Adele can sign in successfully
- MFA is configured
- Identity attributes are accessible for policy evaluation
### Learning resources
- Microsoft Authenticator setup
- Identity security best practices

---

1. In the leftmost pane, go to **Users** > **Active users**.


1. Select **Adele Vance**.



	!IMAGE[tzv4quoo.png](../../media/tzv4quoo.png)

1. At the top of the flyout pane, select **Reset password**.



	!IMAGE[kjwuotbh.png](../../media/kjwuotbh.png)

1. Clear the following checkboxes:



	- **Automatically create a password**
    - **Require this user to change their password...**

1. Enter the following password:



	`rag-sim6` 

1. At the bottom of the pane, select **Reset password**.



	!IMAGE[xanhu383.png](../../media/xanhu383.png)

1. Close the pane.


1. On the VM's taskbar, open Google Chrome, then go to `entra.microsoft.com`.


1. Sign in with **Adele Vance**'s account:



	| Item     | Value                                                |
	|:---------|:---------|
	| Username | `AdeleV@@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).TenantName`       |
	| Password | `rag-sim6`  |

1. Follow the onscreen prompts to use the **Microsoft Authenticator** app to enable MFA.



===

## Task 04: Join GSA VM to Entra
### Introduction
Device identity is just as important as user identity in a Zero Trust model. A trusted device provides context that policies use to determine whether access should be granted.
### Description
The **GSA** VM in your lab will serve as Adele's Entra-joined corporate device in Exercise 02. The Global Secure Access Client requires the device to be Entra-joined, with the user signed in with their Entra account. You'll join a device to Microsoft Entra and associate it with Adele's identity. This creates a trusted endpoint that can be evaluated by Conditional Access and Global Secure Access policies. 
### Example scenario
You're Adele, working from a corporate-issued device. By joining your device to Entra, your organization can securely verify not just who you are-but also that your device meets compliance and trust requirements.
### Success criteria
- Device successfully joined to Entra
- Adele can sign in to the device
- Device is recognized as corporate and trusted
### Learning resources
- Entra device registration concepts

---

1. Switch to the **@lab.VirtualMachine(GSA).SelectLink** virtual machine.



	>[!hint] You can select **@lab.VirtualMachine(GSA).SelectLink** or swap between VMs through the **Resources** tab of this **Instructions** pane.

1. Sign in with the following credentials:



	| Item     | Value                                                |
	|:---------|:---------|
	| Username | **@lab.VirtualMachine(GSA).Username**       |
	| Password | **+++@lab.VirtualMachine(GSA).Password+++** |

1. In the taskbar's search box, enter and select `Access work or school`.


1. Select **Connect**.



	!IMAGE[anzodup3.png](../../media/anzodup3.png)

1. At the bottom of the dialog, select **Join this device to Microsoft Entra ID**.



	!IMAGE[635im3c4.png](../../media/635im3c4.png)

1. Sign in with Adele's credentials:



	| Item     | Value                                                |
	|:---------|:---------|
	| Username | `AdeleV@@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).TenantName` |
	| Password | `rag-sim6` |

1. In the dialog, select **Join**.


1. Once connected, select **Done**.


1. Select the **Start** menu, then select **Admin** > **Sign out**.



	!IMAGE[xbuwy9zb.png](../../media/xbuwy9zb.png)

1. In the lower-left corner of the screen, select **Other user**.


1. Sign in with Adele's Entra credentials:



    | Item | Value |
    |:---------|:---------|
    | Username | +++AdeleV@@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).TenantName+++ |
    | Password | +++rag-sim6+++ |

===

# Exercise 01: Enforce least privileged access
## Scenario
You've just transitioned into a new role as a Senior Product Marketer at Zava. Your access needs have changed overnight. Instead of requesting access manually, your identity is automatically evaluated, and your permissions are updated dynamically.
This exercise demonstrates how identity governance ensures that your access always aligns to your role-no more, no less.
Before you can apply consistent policy to apps and AI, you need automated lifecycle management for users with access and continuous evaluation of whether they should still have it. 
## Objectives- Automate the joiner-mover-leaver lifecycle using lifecycle workflows and access package auto-assignment policies.
- Configure passkey (FIDO2) authentication, Conditional Access risk policies, and access reviews to enforce continuous validation.
- Apply real-time risk signals through ID Protection, Continuous Access Evaluation, and emergency token revocation.
## Duration
Estimated time: 80 minutes

===

## Task 01: Role transfer and automatic provisioning
### Introduction
Identity governance enforces least privilege by continuously aligning access to user attributes. Lifecycle workflows automate this process, ensuring access evolves as roles change-without manual intervention.
### Description
You configure access packages, policies, and workflows that react to attribute changes. When Adele's department changes, her previous access is removed and new access is provisioned automatically.
### Example scenario
You're Adele, and your role changes to Senior Product Marketer. Overnight, your access is updated automatically: outdated permissions are removed, and the tools you need appear instantly. You don't submit a single access request-it's already done.
### Success criteria
- Access package created and assigned
- Old access removed automatically
- New role-based access granted
### Learning resources
- Identity Governance in Microsoft Entra

---

### Key steps

#### 01: Enable FIDO2 passkeys

In this step, you'll configure passkeys (FIDO2) for use in your tenant. Passkeys are phishing-resistant credentials that replace passwords entirely. Users authenticate with the device's biometric or PIN, with no password to type or phish.

1. Switch back to the **@lab.VirtualMachine(Windows11).SelectLink** virtual machine.



	>[!hint] You can select **@lab.VirtualMachine(Windows11).SelectLink** or swap between VMs through the **Resources** tab of this **Instructions** pane.

1. Switch to your Microsoft Edge window.



	>[!hint] Signed in with your lab's admin credentials, not Adele's account.

1. Open a new tab, then go to `entra.microsoft.com`.


1. In the leftmost pane, go to **Entra ID** > **Authentication methods**.



	!IMAGE[8muzctar.png](../../media/8muzctar.png)

1. Select **Passkey (FIDO2)**.



	!IMAGE[s0un2ek1.png](../../media/s0un2ek1.png)

1. Under the **Enable and Target** tab, verify that it's set to **Enable**.



	!IMAGE[ldh9ryi1.png](../../media/ldh9ryi1.png)

1. Near the top of the page, select the **Configure** tab.


1. Verify **Allow self-service setup** is checked.



	>[!knowledge] If disabled, users can't register a passkey from their personal security info page, even if passkeys (FIDO2) are enabled by the authentication methods policy. 

1. At the bottom of the page, select **Save**.



===

#### 02: Review Adele's pre-provisioned attributes

Before configuring the lifecycle controls, you'll take a look at Adele's pre-provisioned attributes the lifecycle automation depends on.

1. In the leftmost pane, go to **Entra ID** > **Users**.


1. Select **Adele Vance**.


1. Copy the value of **Object ID** and paste it in the following text box:



	@lab.TextBox(adeleObjectId)

    !IMAGE[57x58uec.png](../../media/57x58uec.png)

    >[!alert] The pasted value will be referenced in a later task.

1. Under the top bar, select the **Properties** tab.



	!IMAGE[qbzp7fwm.png](../../media/qbzp7fwm.png)

1. Move down to the **Job information** section to observe her current details:



    | Item | Value |
    |---|---|
    | Job title | **Retail Manager** |
    | Department | **Retail** |
    | Manager | **Miriam Graham** |

===

#### 03: Create the access package

An access package bundles the resources a user needs for a specific role (groups, applications, SharePoint sites) along with policies that determine how access is granted. 

1. In the leftmost pane, go to **ID Governance** > **Entitlement management**.


1. In the page's menu, under **Entitlement management**, select **Access packages**.



	!IMAGE[j2xiy34p.png](../../media/j2xiy34p.png)

1. On the top bar, select **New access package**.



	!IMAGE[entah2e8.png](../../media/entah2e8.png)

1. On the **Basics** tab, enter the following:



    | Item | Value |
    |---|---|
    | Name | `IoT PMM Baseline` |
    | Description | `Baseline access for the IoT Product Marketing Manager role.` |
    | Catalog | **General** |

1. Select **Next: Resource roles**.


1. On the **Resource roles** tab, select **Groups and Teams**.



	!IMAGE[mmt1jy66.png](../../media/mmt1jy66.png)

1. In the flyout pane:


1. At the top of the pane, select the checkbox for **See all Group and Team(s)...**



		!IMAGE[qc9wj14j.png](../../media/qc9wj14j.png)

1. In the search box, enter and select `sg-Engineering`.



    	!IMAGE[a81dfrmu.png](../../media/a81dfrmu.png)

1. At the bottom of the pane, choose **Select**.


1. In the **Role** column for **sg-Engineering**, select the dropdown menu, then select **Member**.



	!IMAGE[0ugtpk7e.png](../../media/0ugtpk7e.png)

    >[!knowledge] You're using the existing **sg-Engineering** security group as the resource for the IoT PMM Baseline access package. 

1. Select **Next: Requests**.


1. On the **Requests** tab, under **Who can get access**, keep **None (administrator direct assignments only)**.



    >[!knowledge] You're selecting administrator direct assignments here because access will be granted via the **automatic assignment policy** you'll create next.

1. Under **Approval**, set **Require approval** to **No**.



	!IMAGE[hirf4m5d.png](../../media/hirf4m5d.png)

    >[!knowledge] No approval is needed because no users are requesting this access package. The auto-assignment policy will grant access automatically based on attribute match.

1. Select **Next: Requestor information**.


1. Select **Next: Lifecycle**.


1. On the **Lifecycle** tab, verify the following details:



    | Item | Value |
    |---|---|
    | Access package assignments expire | **Number of days** |
    | Number of days | `365` |

1. Select **Review + create**.


1. Review the configuration, then select **Create**.



	!IMAGE[i4oq7k61.png](../../media/i4oq7k61.png)

>[!knowledge] You added a security group to the package, but access packages can also wrap applications, SharePoint sites, Azure resources, Entra roles, and API permissions for service principal and agent identities.

===

#### 04: Configure the auto-assignment policy

An automatic assignment policy evaluates user attributes against a membership rule and automatically adds or removes them.

1. On the **IoT PMM Baseline** page's menu, select **Policies**.



	
    !IMAGE[uss96lub.png](../../media/uss96lub.png)

1. On the top bar, select **Add auto assignment policy**.



	!IMAGE[xt8hn0ru.png](../../media/xt8hn0ru.png)

1. In the upper-right corner of the **Rule Syntax** box, select **Edit**.



	!IMAGE[varb82hj.png](../../media/varb82hj.png)

1. At the bottom of the page, in the upper-right corner of the **Rule Syntax** box, select **Edit**.



	!IMAGE[msrgo9wh.png](../../media/msrgo9wh.png)

1. In the flyout pane:


1. Enter the following:



    	`(user.department -eq "IoT Marketing")`

1. At the bottom of the pane, select **OK**.


1. Confirm the rule appears in the **Rule syntax** box, then select **Save** at the top of the page.



	
    !IMAGE[xmh013on.png](../../media/xmh013on.png)

1. Verify both checkboxes are selected:



    - **Automatically create assignments**
    - **Automatically remove assignments**

1. Select **Next** until you reach the **Review** tab.


1. On the **Review** tab, enter the following:



    | Item | Value |
    |---|---|
    | Name | `Auto-assign IoT Marketing department users` |
    | Description | `Grants IoT PMM Baseline access to users with Department = IoT Marketing.` |

1. Select **Create**.



    >[!knowledge] Entitlement management additionally creates a unique dynamic security group automatically to evaluate the rule. Do not modify or delete this group.

===

#### 05: Create the mover lifecycle workflow

Lifecycle workflows automate user lifecycle management across the joiner, mover, and leaver phases. The mover workflow you'll create will remove Adele's old access after a role change and notify her manager.

1. In the leftmost pane, go to **ID Governance** > **Lifecycle workflows**.


1. On the top bar, select **Create workflow**.



	!IMAGE[jzl4vtsg.png](../../media/jzl4vtsg.png)

1. In the **Mover** tile for `Employee job profile change`, choose **Select**.



	!IMAGE[1ld8dyjc.png](../../media/1ld8dyjc.png)

1. On the **Basics** tab, enter the following:



    | Item | Value |
    |---|---|
    | Name | `Marketing role transfer mover` |
    | Description | `Removes stale entitlements and notifies the manager when a marketing employee's department changes.` |
    | Trigger type | **Attribute changes** |
    | Trigger attribute | **department** |

    !IMAGE[p6totz4g.png](../../media/p6totz4g.png)

1. Select **Next: Configure scope**.


1. Under the **Rule** section, adjust the following values:



    | Item | Value |
    |---|---|
    | Property | **department** |
    | Operator | **equal** |
    | Value | `IoT Marketing` |

    !IMAGE[6y9q39qj.png](../../media/6y9q39qj.png)

    >[!knowledge] The **trigger** fires when any user's **department** attribute changes. The **scope** filters the trigger so the workflow only runs for users whose new department is set to **IoT Marketing**.

1. Select **Next: Review tasks**.


1. Under the **Workflow tasks** section, select **Remove user from selected groups**.



	!IMAGE[7s8qmvm6.png](../../media/7s8qmvm6.png)

1. In the flyout pane:


1. Select **0 Groups selected**.


    	
        !IMAGE[di9n2rkc.png](../../media/di9n2rkc.png)

1. In the search box, enter and select `sg-Sales and Marketing`.


1. At the bottom of the pane, choose **Select**.


1. At the bottom of the pane, select **Save**.


1. Select **Remove user from selected Teams**.



	!IMAGE[b69ys18f.png](../../media/b69ys18f.png)

1. In the flyout pane:


1. Select **0 Teams selected**.


1. In the search box, enter and select the `Retail` team.


1. At the bottom of the pane, choose **Select**.


1. At the bottom of the pane, select **Save**.


1. Select **Request user access package assignment**.


1. In the flyout pane:


1. Under **Access package**, select **No Access package selected**.


1. Select **IoT PMM Baseline**.



    	!IMAGE[8ya0m6uf.png](../../media/8ya0m6uf.png)

1. At the bottom of the pane, choose **Select**.


1. Under **Policy**, select the dropdown menu, then select **Auto-assign IoT Marketing department users**.



    	!IMAGE[vdr0z7ic.png](../../media/vdr0z7ic.png)

1. At the bottom of the pane, select **Save**.


1. Select **Next: Review + create**.


1. Under the **Schedule workflow** section, select **Enable schedule**.



	!IMAGE[whjnovh4.png](../../media/whjnovh4.png)

	>[!knowledge] By default, workflows are scheduled to run every 3 hours, but you can set the interval to be as frequent as 1 hour or as infrequent as 24 hours.
	>
	>To run the workflow immediately for testing, you'll trigger it manually in a later step.

1. Select **Create**.



===

#### 06: Configure an ML-assisted access review

Access reviews with machine learning-assisted decision recommendations help reviewers make faster, more accurate decisions. 

You'll review membership of the **sg-Engineering** group, which is the resource granted by the IoT PMM Baseline access package. Reviewing this group effectively reviews who has gained access through the package.

1. In the leftmost pane, go to **ID Governance** > **Access reviews**.


1. On the top bar, select **New access review**.



	!IMAGE[l55lcwzj.png](../../media/l55lcwzj.png)

1. In the tile for **Review access to a resource type**, choose **Select**.



	!IMAGE[v33q8bqn.png](../../media/v33q8bqn.png)

1. On the **Select what to review** tab, use the following selections:



    | Item | Value |
    |---|---|
    | Select what to review | **Teams + Groups** |
    | Review scope | **Select Teams + groups** |

1. Choose **Select group(s)**.



	!IMAGE[y95dngn9.png](../../media/y95dngn9.png)

1. In the flyout pane:


1. In the search box, enter and select `sg-Engineering`.


1. At the bottom of the pane, choose **Select**.


1. For **Scope**, select **All users**.



	!IMAGE[zu5padoc.png](../../media/zu5padoc.png)

1. Select **Next: Reviews**.


1. Under **Specify reviewers**:



    | Item | Value |
    |---|---|
    | Select reviewers | **Managers of users** |

1. Under the **Specify recurrence and review** section, enter the following:



    | Item | Value |
    |---|---|
    | Duration (in days) | `7` |
    | Review recurrence | **Quarterly** |	
    | Start date | Keep today's date |
    | End | **Never** |

    !IMAGE[1bkzeopt.png](../../media/1bkzeopt.png)

1. Select **Next: Settings**.


1. On the **Settings** tab, set the following:



    | Item | Value |
    |---|---|
    | Auto apply results to resource | **Enable** |

    !IMAGE[w353bnii.png](../../media/w353bnii.png)

	>[!knowledge] 
	>With **Auto apply results to resource** enabled, accepted decisions are enforced automatically when the review closes. Denied users are removed from **sg-Engineering**, which cascades through the access package to remove their assignment entirely.

1. Under the **Enable reviewer decision helpers** section, enable the following:



    - **No sign-in within 30 days**
    - **User-to-Group affiliation**
    
		!IMAGE[gwuoxmu0.png](../../media/gwuoxmu0.png)

1. Select **Next: Review + Create**.


1. On the **Review + Create** tab, enter the following:



    | Item | Value |
    |---|---|
    | Review name | `sg-Engineering quarterly review` |
    | Description | `Quarterly access review of sg-Engineering members with ML-assisted decision helpers.` |

1. Select **Create**.



===

#### 07: Trigger Adele's role change

In this step, you'll manually update Adele's department directly. In a real-world environment, the customer's HR system could push that role change overnight. 

1. In the leftmost pane, go to **Entra ID** > **Users**.


1. Select **Adele Vance**.


1. On the top bar, select **Edit properties**.



	!IMAGE[rzewyzbg.png](../../media/rzewyzbg.png)

1. Select the **Job Information** tab.


1. Update the following:



    | Item | Value |
    |---|---|
    | Job title | `Senior Product Marketer` |
    | Department | `IoT Marketing` |

    !IMAGE[fwxc7lcx.png](../../media/fwxc7lcx.png)

1. At the bottom of the page, select **Save**.



    >[!note] This change drives the mover workflow via the attribute-change trigger, and the auto-assignment policy via the membership rule.

===

#### 08: Run the mover workflow on demand

Scheduled lifecycle workflows check execution conditions every three hours by default. You'll run the workflow on-demand against Adele.

1. In the leftmost pane, go to **ID Governance** > **Lifecycle workflows**.


1. In the **Lifecycle workflows** page's menu, select **Workflows**.



	!IMAGE[lkfzb7af.png](../../media/lkfzb7af.png)

1. Select **Marketing role transfer mover**.


1. On the top bar, select **Run on demand**.



	
	!IMAGE[u71nn2hs.png](../../media/u71nn2hs.png)

1. Choose **Select users**.


1. In the flyout pane:


1. Select `Adele Vance`.


1. At the bottom of the pane, choose **Select**.


1. At the bottom of the page, select **Run workflow**.



	!IMAGE[h2yx7am9.png](../../media/h2yx7am9.png)

	>[!note] This will take you to the **Workflow history** page.

1. On the top bar, periodically select **Refresh** until the run for Adele appears.



	!IMAGE[jis9vfqf.png](../../media/jis9vfqf.png)

1. Select **Adele Vance** to view the task results.


1. Observe the tasks it ran in the flyout pane. All tasks should show **Completed**.



	!IMAGE[43a2xooe.png](../../media/43a2xooe.png)

	>[!alert] If it's not finished, refresh the table and try again. If it hangs for over five minutes, try running the workflow again.

===

#### 09: Verify auto-assignment

1. In the leftmost pane, go to **ID Governance** > **Entitlement management**.


1. In the page's menu, under **Entitlement management**, select **Access package**.


1. Select **IoT PMM Baseline**.



	!IMAGE[7vn1d1bo.png](../../media/7vn1d1bo.png)

1. In the page's menu, select **Assignments**.


1. On the entry for Adele Vance, observe the **Policy** column shows **Auto-assign IoT Marketing department users**.



	!IMAGE[udlz2sw6.png](../../media/udlz2sw6.png)

    >[!alert] It may take around five minutes to evaluate the new department attribute and create the assignment. Select **Refresh** on the top bar periodically.

1. In the leftmost pane, go to **Entra ID** > **Users**.


1. Select **Adele Vance**.


1. In the page's menu, select **Groups**.



	!IMAGE[l4s0fuhu.png](../../media/l4s0fuhu.png)

1. Confirm Adele is now part of **sg-Engineering**.


1. Confirm she's no longer a member of:



	- **Retail**
    - **sg-Sales and Marketing**

>[!knowledge] Access follows attribute, attribute follows reality, and provisioning is automatic and auditable.
>
>Each time Adele's group memberships change, Conditional Access re-evaluates her scope on her next token request. Policies that target **sg-Engineering** members now apply to her. Policies that targeted **sg-Sales and Marketing** no longer do.

===

## Task 02: Risk detection and real-time token revocation

### Introduction
Trust must be continuously evaluated. Risk-based policies ensure that compromised identities are detected and controlled in real time.
### Description
In this task, you'll tour ID Protection, configure Conditional Access risk policies, and review how Continuous Access Evaluation enforces real-time revocation. You configure risk-based Conditional Access policies and simulate a high-risk scenario. When Adele's account is flagged, access is immediately restricted, and active sessions are revoked.
### Example scenario
You're Adele, working normally when your account is suddenly flagged as high risk due to suspicious sign-in activity. Instantly, your sessions are revoked, and you're prompted to reauthenticate-protecting your data before any damage occurs.
### Success criteria
- Risk policies triggered successfully
- Sessions revoked in real time
- Secure reauthentication enforced
Learning resources
- Identity Protection and CAE

---

### Key steps

#### 01: Configure the user risk Conditional Access policy

>[!knowledge] **User risk** represents the cumulative likelihood that an account has been compromised over time. A user-risk policy responds to elevated user risk by requiring strong reauthentication before allowing access.

1. In the leftmost pane, go to **Entra ID** > **Conditional Access**.


1. On the top bar, select **Create new policy**.



	!IMAGE[wupfl4dq.png](../../media/wupfl4dq.png)

1. In the **Name** box, enter:



	`CA01 - Require MFA for high user risk`

1. Under **Users or agents**, select **0 users or agents selected**.


1. Under **Include**, select **All users**.



    	!IMAGE[1ktx2vkr.png](../../media/1ktx2vkr.png)

1. Select the **Exclude** tab.


1. Select the **Users and groups** checkbox.


1. Enter and select `@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).AdministrativeUsername`.



        >[!knowledge] Always exclude break-glass and admin accounts from risk-based policies to prevent lockout.

1. At the bottom of the pane, choose **Select**.



    	!IMAGE[3e13nx6o.png](../../media/3e13nx6o.png)

1. Under **Target resources**, select **No target resources selected**.


1. Under **Include**, select **All resources (formerly 'All cloud apps')**.



    	!IMAGE[58ecto4d.png](../../media/58ecto4d.png)

1. Under **Conditions**, select **0 conditions selected**.


1. Under **User risk**, select **Not configured**.


1. In the flyout pane, set **Configure** to **Yes**.


1. Select **High**.



    	!IMAGE[nvgljx18.png](../../media/nvgljx18.png)

1. At the bottom of the pane, select **Done**.


1. Under **Grant**, select **0 controls selected**.


1. In the flyout pane, select **Grant access**.


1. Select the **Require authentication strength** checkbox, then verify **Multifactor authentication** is selected.



    	!IMAGE[yfgdquw1.png](../../media/yfgdquw1.png)

1. At the bottom of the pane, choose **Select**.



        >[!knowledge] In a real-world environment, Microsoft recommends pairing the user risk policy with **Require risk remediation**, which runs a secure password change or strong reauthentication flow that automatically clears the user's risk state. 

1. Set **Enable policy** to **On**.



	!IMAGE[kklgcmp4.png](../../media/kklgcmp4.png)

1. At the bottom of the page, select **Create**.



===

#### 02: Configure the sign-in risk Conditional Access policy

Sign-in risk represents the likelihood a specific authentication request isn't from the legitimate user. A sign-in risk policy responds in real time to a suspicious sign-in.

1. On the top bar, select **Create new policy**.


1. In the **Name** box, enter:



	`CA02 - Require MFA for high or medium sign-in risk`

1. Under **Users or agents**, select **0 users or agents selected**.


1. Under **Include**, select **All users**.


1. Select the **Exclude** tab.


1. Select the **Users and groups** checkbox.


1. Enter and select `@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).AdministrativeUsername`.


1. At the bottom of the pane, choose **Select**.



    !IMAGE[a2zpy39i.png](../../media/a2zpy39i.png)

1. Under **Target resources**, select **No target resources selected**.


1. Under **Include**, select **All resources (formerly 'All cloud apps')**.


1. Under **Conditions**, select **0 conditions selected**.


1. Under **Sign-in risk**, select **Not configured**.



    	!IMAGE[517nsagg.png](../../media/517nsagg.png)

1. In the flyout pane, set **Configure** to **Yes**.


1. Select **High** and **Medium**.



    	!IMAGE[cf4j6h3f.png](../../media/cf4j6h3f.png)

1. At the bottom of the pane, select **Done**.


1. Under **Grant**, select **0 controls selected**.


1. In the flyout pane, select **Grant access**.


1. Select the **Require authentication strength** checkbox, then verify **Multifactor authentication** is selected.


1. At the bottom of the pane, choose **Select**.


1. Set **Enable policy** to **On**.



	!IMAGE[nb2ercmo.png](../../media/nb2ercmo.png)

1. At the bottom of the page, select **Create**.



===

#### 03: Simulate a risk detection on Adele

You'll manually elevate Adele's user risk to **High** to simulate a risk detection and trigger the **CA01** policy.

1. In a new browser tab, go to `developer.microsoft.com/graph/graph-explorer`.


1. In the upper-right corner of the page, select the **Sign in** icon.



	!IMAGE[9cqczkmq.png](../../media/9cqczkmq.png)

1. In the dialog, select **@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).AdministrativeUsername**.


1. In the permissions dialog, select **Accept**.



	!IMAGE[2awm345q.png](../../media/2awm345q.png)

1. At the top of the page, configure the request:



	| Item | Value |
	|---|---|
	| HTTP method | **POST** |
	| API version | **v1.0** |
	| URL | `https://graph.microsoft.com/v1.0/identityProtection/riskyUsers/confirmCompromised` |

    !IMAGE[0lbplav1.png](../../media/0lbplav1.png)

1. Below the URL, in the **Request Body** box, enter the following JSON:



	>[!hint] Select **Copy** on the following code block, then paste with **Ctrl+V**.

    
json
    {
        "userIds": ["@lab.Variable(adeleObjectId)"]
    }
    ```

    >[!alert] This uses Adele's **Object ID**, which you pasted in the text box in an earlier task.

1. Below the URL, select the **Modify Permissions** tab.



	!IMAGE[m2ga9bp4.png](../../media/m2ga9bp4.png)

1. On the line for **IdentityRiskyUser.ReadWrite.All**, select **Consent**.



	!IMAGE[dtdyeer5.png](../../media/dtdyeer5.png)

1. In the permissions dialog, select **Accept**.


1. To the right of the **URL**, select **Run query**.


1. Confirm the response shows **No Content - 204** below the permissions body, indicating the action succeeded.



	!IMAGE[ygqx6lnl.png](../../media/ygqx6lnl.png)

	>[!alert] If you receive an error, verify Adele's **Object ID** is set in the **Request Body** tab.

1. Switch back to your Microsoft Entra admin center tab.


1. In the leftmost pane, go to **ID Protection** > **Risky users**.


1. Move to the bottom of the page and verify **Adele Vance** appears in the table. Observe the results. 



	!IMAGE[eaoymb5d.png](../../media/eaoymb5d.png)

	>[!alert] It may take a few minutes for her account to appear. Periodically refresh the page.

1. In the **Security** page's menu, under **Report**, select **Risk detections**.


1. Select the date under the **Detection time** column and observe the results in the flyout pane.



	!IMAGE[tsr00f8o.png](../../media/tsr00f8o.png)

===

#### 04: Revoke Adele's sessions

When an account is suspected to be compromised, an admin like the SOC Analyst can immediately invalidate all of the user's active refresh tokens using the **Revoke sessions** action. 

1. In the leftmost pane, go to **Entra ID** > **Users**.


1. Select **Adele Vance**.


1. On the top bar, select **Revoke sessions**.



	!IMAGE[bll09mko.png](../../media/bll09mko.png)

1. In the confirmation dialog, select **Yes**.


1. Switch back to your **Google Chrome** window where Adele is signed in.


1. Open a new tab, then go to `myapps.microsoft.com`.


1. Observe Adele is redirected back to the sign-in page immediately upon the admin's revocation.


1. Sign back in with Adele's credentials:



	| Item     | Value                                                |
	|:---------|:---------|
	| Username | `AdeleV@@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).TenantName` |
	| Password | `rag-sim6` |

	>[!knowledge] **Continuous Access Evaluation (CAE)** propagates Entra ID's revocation event to CAE-capable resource providers like Exchange Online, SharePoint, Teams, and Microsoft Graph in near real-time.

===

#### 05: Verify CA01 fired on Adele's sign-in

1. Switch back to your **Microsoft Edge** window.


1. In the leftmost pane, go to **Entra ID** > **Monitoring & health** > **Sign-in logs**.



	>[!alert] You'll need to wait around five minutes for Adele's latest sign-in. Periodically select **Refresh** above the table.

1. Select the latest successful sign-in **Date** for **adelev@@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).TenantName**.



	!IMAGE[nz5yuv4z.png](../../media/nz5yuv4z.png)

1. At the top of the flyout pane, select the **Conditional access** tab.


1. Observe the **CA01 - Require MFA for high user risk** policy was triggered and shows **Success**.



	!IMAGE[u55wo8fb.png](../../media/u55wo8fb.png)

===

#### 06: Dismiss residual risk

1. In the leftmost pane, go to **ID Protection** > **Risky users**.


1. Move to the bottom table, then select **Adele Vance**.



	!IMAGE[6cl95unp.png](../../media/6cl95unp.png)

1. Observe Adele's **Risk Level**, and the **Timeline** tile.


1. On the top bar, select **Confirm user(s) safe**.



	!IMAGE[v04op2o7.png](../../media/v04op2o7.png)

1. In the dialog, select **Yes**.



	>[!note] After a few minutes Adele's risk state will be reset to **None**. You can proceed to the next task without waiting.

---

Adele's group memberships now follow her department attribute through an access package, a mover workflow cleans up her old access automatically, and a quarterly ML-assisted review keeps the resulting membership honest over time. 

On the response side, two risk-based Conditional Access policies and CAE-driven session revocation give admins a real-time control plane for compromised accounts. The same policy engine governs both, with one audit trail across Entra ID, ID Protection, and Lifecycle Workflows.

===

# Exercise 02: Modernize access to any app

## Scenario
You need access to a critical on-premises application to complete your analysis. Traditionally, this would require a VPN. Instead, your organization uses identity-based access to connect you directly-securely and seamlessly.
In this exercise, you'll broker on-prem access through Global Secure Access (GSA) Private Access so the same policy engine that governs cloud apps also governs an internal Zava Finance Portal site. You'll then layer just-in-time access controls on top for sensitive data.
## Objectives- Replace legacy VPNs with identity-based, per-app access to on-premises applications using **Global Secure Access Private Access**.
- Apply Conditional Access policies to on-prem resources, eliminating the parallel security plane of traditional VPN deployments.
- Configure just-in-time, time-bound access to sensitive resources with multi-stage approval and recurring access reviews.
- Understand how **Verified ID** raises the assurance bar for sensitive access requests beyond credentials and MFA alone.

## Duration
Estimated time: 110 minutes

===

## Task 01: Broker on-prem access through Private Access
### Introduction
Identity-based network access replaces traditional network perimeter controls. Applications are exposed securely through identity rather than network location.
### Description
You configure Private Access, enabling secure connectivity to an on-prem application without exposing it to the internet.
GSA Private Access replaces traditional VPNs with per-app Zero Trust Network Access. You'll configure three parts:
- **Private Access connector** - runs on a Windows server inside the private network and connects outbound to GSA with no inbound firewall ports.
- **Application segment** - defines what's exposed (FQDN/IP, port, protocol).
- **Enterprise application** - the Entra ID identity representation of the on-prem app, which you can then target with Conditional Access and user assignments.
### Example scenario
You're Adele, needing access to Zava's internal finance system. Instead of launching a VPN, you simply open your browser-and your identity is used to securely broker access to the application.
### Success criteria
- Private Access configured
- App published securely
- Adele assigned access
### Learning resources
- Global Secure Access overview

---

### Key steps

#### 01: Test connection to the on-prem application

1. Switch to the **@lab.VirtualMachine(GSA).SelectLink** VM.


1. Open Microsoft Edge.


1. In the dialog, select **Confirm and continue**.


1. Select **Continue without Google data**.


1. If prompted to sign in, use Adele's credentials:



    | Item | Value |
    |---|---|
    | Email | `AdeleV@@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).TenantName` |
    | Password | `rag-sim6` |

1. In the address bar, go to `pim.zava.internal`.


1. Observe the page fails to load.



	>[!note] **pim.zava.internal** is an on-prem-only FQDN. No public DNS resolves it, and no traffic from this workstation reaches the on-prem server hosting it. This is the everyday state of every on-prem app inside Zava's corporate network.

1. Select the **Start** menu, then select **Adele Vance** > **Sign out**.



	!IMAGE[kry8piqj.png](../../media/kry8piqj.png)

===

#### 02: Install the Private Access connector on the on-premises server

The Private Access connector is the on-prem half of the brokered connection. You'll install it on the **Windows Server 2025** VM, which represents Zava's on-premises data center hosting the Zava Finance Portal application.

>[!note] The server has been pre-configured to act as the on-prem host for the Zava Finance Portal:
>
>- **IIS** runs a site named **ZavaPIM** located at `C:\inetpub\zavapim`. The site hosts a small static web app.
>- The IIS binding is **pim.zava.internal** on port 80.
>- A **hosts** file entry on the server (**127.0.0.1 pim.zava.internal**) lets local IIS resolve its own FQDN.

1. Switch to the **@lab.VirtualMachine(WindowsServer2025).SelectLink** virtual machine.


1. Sign in with the following credentials:



    | Item     | Value                                                |
    |:---------|:---------|
    | Username | **@lab.VirtualMachine(WindowsServer2025).Username**       |
    | Password | **+++@lab.VirtualMachine(WindowsServer2025).Password+++** |

1. On the desktop, open **MicrosoftEntraPrivateNetworkConnectorInstaller**.



	!IMAGE[1ct2dr2i.png](../../media/1ct2dr2i.png)

1. Accept the license terms, then select **Install**.


1. When prompted, sign in with your lab's admin credentials to connect it to your tenant:



    | Item     | Value                                                |
    |:---------|:---------|
    | Username | `@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).AdministrativeUsername` |
    | Password | `@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).AdministrativePassword` |

1. After setup, select **Close**.



	!IMAGE[mcyo4zun.png](../../media/mcyo4zun.png)

1. Switch back to the **@lab.VirtualMachine(Windows11).SelectLink** virtual machine.


1. In Entra's leftmost pane, go to **Global Secure Access** > **Connect** > **Connectors and sensors**.


1. In the top banner, select **Activate**.



	!IMAGE[qta2in10.png](../../media/qta2in10.png)

1. Once activated, in the leftmost pane, go to **Global Secure Access** > **Connect** > **Connectors and sensors**.



	!IMAGE[71t9i13v.png](../../media/71t9i13v.png)

    >[!note] The connector's **Status** should show **Active**. The connector is automatically added to the **Default** connector group.

===

#### 03: Enable Private Access traffic forwarding

Traffic forwarding profiles control which categories of traffic the Global Secure Access client routes through GSA. Three profiles exist: **Microsoft traffic**, **Private access**, and **Internet access**, which can be enabled independently. 

1. In the leftmost pane, go to **Global Secure Access** > **Connect** > **Traffic forwarding**.


1. Turn on **Private access profile**.


1. In the dialog, select **OK**.



    >[!note] Devices with the Global Secure Access client installed will pick up the updated forwarding profile within a few minutes. 

1. In the **Private access profile** tile, under **User and group assignments**, select **View**.



	!IMAGE[xpz1qc5b.png](../../media/xpz1qc5b.png)

1. In the flyout pane:


1. Enable **Assign to all users**.


1. In the dialog, select **OK**.



    	!IMAGE[ojtrswln.png](../../media/ojtrswln.png)

		>[!knowledge] In production, you could add a security group representing your phased GSA rollout.

1. At the bottom of the pane, select **Done**.



	!IMAGE[ll5kvu42.png](../../media/ll5kvu42.png)

===

#### 04: Create the Zava Finance Portal enterprise application and application segment

Now you'll publish the on-prem Zava Finance Portal site as an enterprise application with an application segment defining its FQDN, port, and protocol.

1. In the leftmost pane, go to **Global Secure Access** > **Applications** > **Enterprise applications**.


1. On the top bar, select **New application**.



	!IMAGE[d3zobbft.png](../../media/d3zobbft.png)

1. Enter the following details:



    | Item | Value |
    |---|---|
    | Name | `Zava Finance Portal` |
    | Connector group | **Default - North America** |

	>[!note] The default connector group contains the connector you registered from **Windows Server 2025**.

1. Under the **Application segment** section, select **Add application segment**.



	!IMAGE[up20gdu8.png](../../media/up20gdu8.png)

1. In the flyout pane, enter the following details:



    | Item | Value |
    |---|---|
    | Destination type | **Fully qualified domain name** |
    | Fully qualified domain name | `pim.zava.internal` |
    | Ports | `80` |
    | Protocol | **TCP** |

    !IMAGE[gw3e3xyk.png](../../media/gw3e3xyk.png)

	>[!note] The FQDN must match what end users will type in their browser. The connector on **Windows Server 2025** resolves this FQDN locally via its **hosts** file and relays the request to the IIS site running there. 
	
	>[!knowledge] The GSA service handles DNS resolution for the client side, so end users don't need a **hosts** file entry or DNS reachability on their own device.

1. At the bottom of the pane, select **Apply**.


1. At the bottom of the page, select **Save**.



	!IMAGE[hc0u38uk.png](../../media/hc0u38uk.png)

1. Once finished, in the leftmost pane, go back to **Global Secure Access** > **Applications** > **Enterprise applications**.


1. Select the **Zava Finance Portal** application you just created.



	!IMAGE[1a4xza36.png](../../media/1a4xza36.png)

	>[!alert] It may take a minute to appear. Periodically select **Refresh** on the top bar.

1. In the application page's menu, under the **Manage** section, select **Users and groups**.


1. On the top bar, select **Add user/group**.



	!IMAGE[xilnmgil.png](../../media/xilnmgil.png)

1. Under **Users and groups**, select **None Selected**.


1. In the flyout pane:


1. In the search box, enter and select `Adele Vance`.


1. At the bottom of the pane, choose **Select**.


1. At the bottom of the page, select **Assign**.



	>[!knowledge] Assignments to enterprise apps are generally group-based rather than direct assignments. As users join, transfer, or leave a group, their access to an app (like Zava Finance Portal) would then follow their group membership automatically.

===

## Task 02: Access the Zava Finance Portal
### Introduction
User access should be seamless when identity is trusted. The system transparently applies policies without adding friction.
### Description
You access the on-prem app as Adele, validating that your identity and device are sufficient to gain access without VPN.
The Global Secure Access client must run on a Microsoft Entra-joined or hybrid-joined device, signed in with a Microsoft Entra account.
### Example scenario
You're Adele, retrieving pricing data. You simply open the application link, and it loads-securely and directly-without any network complexity.
### Success criteria
- App accessible via browser
- No VPN required
- Identity-based access enforced
### Learning resources
- Zero Trust network access

---

### Key steps

#### 01: Verify connection to the Global Secure Access client

The GSA client has been pre-installed on the **GSA** VM. It runs as a Windows service and signs in as the user signed in to the device. It then applies the traffic forwarding profiles configured on the tenant.

1. Switch to the **@lab.VirtualMachine(GSA).SelectLink** virtual machine.


1. In the lower-left corner of the screen, select **Other user**.


1. Sign in with Adele's Entra credentials:



    | Item | Value |
    |:---------|:---------|
    | Username | +++AdeleV@@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).TenantName+++ |
    | Password | +++rag-sim6+++ |

1. In the lower-right corner of the screen, expand the system tray, then select the **Global Secure Access** icon.



	!IMAGE[knk62egu.png](../../media/knk62egu.png)

1. The **Status** should show **Connected**.



	!IMAGE[wvedq3qg.png](../../media/wvedq3qg.png)

	>[!alert] If it shows **Disabled by your organization**:
	>
	>1. In the leftmost pane, select **Troubleshooting**.
	>1. Under **Get latest policy**, select **Get policy**.
	>
	>	!IMAGE[j9jtjafq.png](../../media/j9jtjafq.png)
	>	!IMAGE[xhuufd2v.png](../../media/xhuufd2v.png)
	>
	>	If you receive a **No policy** message, wait a few minutes, then try again.
    >
	>1. In the leftmost pane, go back to **Connections**.

1. To ensure you have the latest policies, in the leftmost pane, select **Troubleshooting**.


1. Under **Get latest policy**, select **Get policy**.



	!IMAGE[j9jtjafq.png](../../media/j9jtjafq.png)
	!IMAGE[xhuufd2v.png](../../media/xhuufd2v.png)

===

#### 02: Access the Zava Finance Portal through Private Access

1. Open **Microsoft Edge**, then go to `pim.zava.internal`.



	>[!alert] If the site fails to load, wait a few minutes for the policy to finish applying and try again.

	>[!knowledge] The Global Secure Access client intercepts the request, brokers it through GSA, and the connector on **Windows Server 2025** relays it to the on-prem IIS site it hosts. 

1. Enter the following credentials:



    | Item | Value |
    |---|---|
    | Email | `AdeleV@@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).TenantName` |
    | Password | `rag-sim6` |

	!IMAGE[chn50k3i.png](../../media/chn50k3i.png)

1. Select a few menu items in the leftmost pane to generate more traffic.



	!IMAGE[kkalupsp.png](../../media/kkalupsp.png)

===

#### 03: View the GSA dashboard

The GSA dashboard provides visualizations of the network traffic that the Microsoft Entra Private Access and Microsoft Entra Internet Access services acquire. 

1. Switch back to the **@lab.VirtualMachine(Windows11).SelectLink** virtual machine.


1. In the leftmost pane, go to **Global Secure Access** > **Dashboard**.


1. Observe the widgets the dashboard provides.



	!IMAGE[88o8tzck.png](../../media/88o8tzck.png)

	>[!knowledge]For more details on specific tiles, visit the following:
	> - [Global Secure Access snapshot](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-traffic-dashboard#global-secure-access-snapshot)
	> - [Usage profiling](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-traffic-dashboard#global-secure-access-snapshot)
	> - [Top used cloud applications](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-traffic-dashboard#global-secure-access-snapshot)
	> - [Network activity by location](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-traffic-dashboard#global-secure-access-snapshot)
	> - [Cloud applications status](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-traffic-dashboard#global-secure-access-snapshot)
	> - [Web category filtering](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-traffic-dashboard#global-secure-access-snapshot)
	> - [Top used destinations](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-traffic-dashboard#global-secure-access-snapshot)
	> - [External tenant access](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-traffic-dashboard#global-secure-access-snapshot)
	> - [Device status](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-traffic-dashboard#global-secure-access-snapshot)
	> - [Alerts](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-traffic-dashboard#global-secure-access-snapshot)
	> - [Alerts and notifications](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-traffic-dashboard#global-secure-access-snapshot)

===

#### 04: Observe Global Secure Access traffic logs

Traffic logs capture every transaction flowing through GSA. SOC and operations teams can use this as the source for who accessed what, from where, when, and with what result.

1. In the leftmost pane, go to **Global Secure Access** > **Monitor** > **Traffic logs**.


1. Above the table, select the **Transactions** tab.



	!IMAGE[4ubi5q3m.png](../../media/4ubi5q3m.png)

1. Below the top bar, select the **Private Access** tile to quickly filter by traffic type.



	!IMAGE[o041bq5c.png](../../media/o041bq5c.png)

1. Observe Adele's transactions to **pim.zava.internal** in the log table, with the **Traffic type** column showing **Private**.



	!IMAGE[qv6xmqtw.png](../../media/qv6xmqtw.png)

	>[!alert] It may take a couple minutes to appear.

1. On the top bar, select **Columns** to observe the available columns that can be added to the view.


1. Close the flyout pane without making changes.


1. The **Connections** tab will take more time to populate data. You can proceed to the next task.



	>[!knowledge] Traffic logs operate at three conceptual levels: 
	>- **Session** - A user's logical browsing flow.
	>- **Connection** - Source/destination IP, source/destination port, and fully qualified domain name (FQDN).
	>- **Transaction** - A single request/response pair. 
	>
	>Only **Connections** and **Transactions** are surfaced in the UI.

===

## Task 03: Just-in-time access with multi-stage approval
### Introduction
Sensitive data requires additional controls. Just-in-time access ensures elevated permissions are granted only when needed-and for limited duration.
### Description
You configure a request-based access package with approvals and expiration. Adele must request access and receive approval before accessing sensitive data. You'll configure a sensitive access package that grants access to confidential pricing data with multi-stage approval, time-bound assignment, and a recurring access review.
### Example scenario
You're Adele, preparing a Q4 analysis. You request access to confidential pricing data. Your request is approved in stages, your identity is verified, and access is granted temporarily-just long enough to complete your work.
### Success criteria
- Access request completed
- Approval workflow executed
- Time-bound access granted
### Learning resources
- Access packages and approvals

---

1. In the leftmost pane, go to **ID Governance** > **Entitlement management**.


1. In the page's menu, under **Entitlement management**, select **Access packages**.


1. On the top bar, select **New access package**.



	!IMAGE[epulh4cy.png](../../media/epulh4cy.png)

1. On the **Basics** tab, enter the following:



    | Item | Value |
    |---|---|
    | Name | `Zava Assistant - Confidential Pricing Data` |
    | Description | `Just-in-time access to Zava Finance's confidential pricing data for marketing analysis. Requires multi-stage approval.` |
    | Catalog | **General** |

1. Select **Next: Resource roles**.


1. On the **Resource roles** tab, select **Groups and Teams**.



	!IMAGE[ot1jahqk.png](../../media/ot1jahqk.png)

1. In the flyout pane:


1. At the top of the pane, select the checkbox for **See all Group and Team(s)...**


1. In the search box, enter and select `sg-Finance`.


1. At the bottom of the pane, choose **Select**.


1. In the **Role** column for **sg-Finance**, select the dropdown menu, then select **Member**.



	!IMAGE[62tdca6r.png](../../media/62tdca6r.png)

1. Select **Next: Requests**.


1. On the **Requests** tab, enter the following:



    | Item | Value |
    |---|---|
    | Who can get access | **For users, service principals and agent...** |
    | Select Specific scope | **All members (excluding guests)** |
    | Who can request access | **Self** |
    | How many stages? | **2** |

	!IMAGE[ojcbw7ip.png](../../media/ojcbw7ip.png)

    >[!knowledge] Unlike the IoT PMM Baseline package in Exercise 01, this package is user-requestable. 

1. Under the **First Approver** section's dropdown menu, select **Choose specific approvers**.


1. Select **Add approvers**.



	!IMAGE[bpdmzwnq.png](../../media/bpdmzwnq.png)

1. In the flyout pane:


1. Enter and select `@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).AdministrativeUsername`.


1. At the bottom of the pane, choose **Select**.



    >[!knowledge] In a real-world environment, the first approver would likely be kept as **Manager as approver**. You'll streamline the process in this exercise just to observe the flow.

1. Under the **Second Approver** section's dropdown menu, keep **Choose specific approvers**.


1. Select **Add approvers**.


1. In the flyout pane:


1. Enter and select `@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).AdministrativeUsername`.


1. At the bottom of the pane, choose **Select**.



	!IMAGE[80h2tz8g.png](../../media/80h2tz8g.png)

    >[!knowledge] In a real-world environment, the second approver might be the data owner or anyone responsible for the data being accessed. 

1. Select **Next: Requestor information**.


1. Select **Next: Lifecycle**.


1. On the **Lifecycle** tab, enter the following:



    | Item | Value |
    |---|---|
    | Access package assignments expire | **Number of days** |
    | Assignments expire after | `180` |

	!IMAGE[3xyjwg9v.png](../../media/3xyjwg9v.png)

    >[!note] Adele's access automatically expires after 180 days. If she still needs access, she'd submit a new request to go through the approval flow again.

1. Under **Access Reviews**, select the **Require access reviews** checkbox.


1. Enter the following details:



    | Item | Value |
    |---|---|
    | Starting on | Keep today's date |
    | Review frequency | **Quarterly** |
    | Duration (in days) | `7` |
    | Reviewers | **Self-review** |

	!IMAGE[tckpyw19.png](../../media/tckpyw19.png)

    >[!knowledge] **Self-review** asks each assignee whether they still need their access. For perpetual baseline packages, **Specific reviewers** (a data owner or manager) may be more appropriate.

1. Select **Show advanced access review settings**.



	>[!alert] You may need to select it twice.

1. Set **If reviewers don't respond** to **Remove access**.



	!IMAGE[x46lgp9t.png](../../media/x46lgp9t.png)

    >[!note] If Adele forgets to respond to her own review, her access is automatically removed. Combined with the 180-day expiration, these are two independent mechanisms preventing stale access from persisting.

1. Select **Review + create**.


1. Review the configuration, then select **Create**.



===

## Task 04: Request and approve access packages

In this task, you'll act as Adele requesting the Zava Assistant access package through the My Access portal, run through the approval process, then confirm her time-bound access is granted.

---

### Key steps

#### 01: Request the Zava Assistant access package

**My Access** is the user-facing portal for access requests in Microsoft Entra ID Governance. Users can browse available access packages, submit requests with justification, and track the status of their requests through approval.

1. Switch to your **Google Chrome** window where Adele is signed in.


1. Open a new tab, then go to `https://myaccess.microsoft.com`.


1. In the leftmost pane, go to **My Access** > **Access packages**.


1. Select **View all**.



	!IMAGE[8pjgw0ng.png](../../media/8pjgw0ng.png)

1. Select **Zava Assistant - Confidential Pricing Data**.



	
	!IMAGE[7lkk3dwb.png](../../media/7lkk3dwb.png)

1. In the dialog:


1. Select the **Resources** tab to see what you'll be granted.


1. At the bottom of the dialog, select **Continue**.


1. In the **Business justification** box, enter:



    `Q4 IoT competitive analysis - need access to historical pricing data for upcoming VP presentation.`

1. Select **Submit request**.



	!IMAGE[vj15rg9u.png](../../media/vj15rg9u.png)

===

#### 02: Approve the request through both stages

1. Switch to your Microsoft Edge window signed in with the admin account.


1. Open a new tab, then go to `https://myaccess.microsoft.com`.



    >[!note] The same portal is used by both requesters and approvers.

1. Under **Your pending actions**, select **Approve or deny now**.



	!IMAGE[53qu7m9f.png](../../media/53qu7m9f.png)

1. On the line for Adele's request, select **Review**.



	!IMAGE[lbboz6h8.png](../../media/lbboz6h8.png)

1. In the flyout pane:


1. Observe the information.


1. Select **Request details** to see details like the business justification.


1. At the top of the pane, select **Review request** to go back.


1. Under **Decision**, select **Approve**.


1. Under **Provide reason**, enter the following:



    	`Manager approval. Justification valid for the Q4 deliverable.`

		!IMAGE[2sz9z8h3.png](../../media/2sz9z8h3.png)

1. At the bottom of the pane, select **Submit**.



    	>[!note] The second stage of approval will then be triggered.

1. Refresh the page to view the second approval request in the list.


1. Repeat the steps for approval, but use the following in the **Provide reason** box:



    `Data owner approval. Access scoped to 180 days per package policy.`


===

#### 03: Confirm Adele's time-bound access is granted

1. Switch back to your **Google Chrome** window where Adele is signed in.


1. In the leftmost pane, go to **My Access** > **Access packages**.


1. Select the **Active** tab.


1. Confirm **Zava Assistant - Confidential Pricing Data** appears with an expiration date 180 days from now.



	!IMAGE[8lus6rc7.png](../../media/8lus6rc7.png)

	>[!alert] It may take a minute to appear. Refresh the page.

===

## Task 05: Verified ID

For sensitive resources, proving who is actually requesting access matters more than proving the credentials are valid. Stolen credentials, session hijacks, and AI-generated impersonation can defeat traditional MFA. Verified ID with Face Check binds the request to a cryptographically signed, photo-matched verifiable credential.

>[!knowledge] [Introduction to Microsoft Verified ID](https://learn.microsoft.com/en-us/entra/verified-id/decentralized-identifier-overview)

---

Watch the following videos to see in-depth examples of how admins could configure parts of Verified ID.

1. Part one:



	!video[Verified ID - Part One](https://www.youtube.com/watch?v=Uy6vWSuKDDI)

1. Part two:



	!video[Verified ID - Part Two](https://www.youtube.com/watch?v=oc5HaIUUehs)

    >[!knowledge] 
    >With Verified ID, the **Requests** tab of the access package creation wizard you used earlier exposes a **Required Verified IDs** section that can be configured.

---

The Zava Finance Portal site is now governed by the same Conditional Access policy engine as every cloud app on the tenant. No VPN, no inbound firewall ports, no parallel security plane. 

Sensitive resources sit behind multi-stage approval, time-bound assignments, and a recurring review.

===

# Exercise 03: Enable safe AI access
## Scenario
AI access is the latest attack surface and the one that bypasses traditional controls most easily. Browser-based LLM sessions exfiltrate data through file uploads, MCP-speaking clients reach external servers without IT visibility, and prompt injection defeats application-layer guardrails. 
In this exercise, you'll bring all three under GSA using TLS inspection, data loss prevention (DLP), and prompt injection protection for users, while using the Secure Web and AI Gateway integration for Copilot Studio agents.

## Objectives- Route user internet traffic through GSA and apply TLS inspection so the inline proxy can scan encrypted web payloads.
- Block sensitive file uploads from unsanctioned destinations using network DLP content policies.
- Learn about Model Context Protocol (MCP) traffic flowing to remote AI servers using Gen AI Insights logs.
- Bring Copilot Studio agent traffic under network-layer security controls.
- Block adversarial prompts to enterprise LLMs using prompt injection protection before the prompts reach the model.
## Duration
Estimated time: 40 minutes

===

## Task 01: Block confidential file uploads
### Introduction
In this task, you'll route end-user internet traffic through GSA, enable TLS inspection to inspect encrypted web traffic, and create a content policy that blocks risky file uploads to unsanctioned destinations.
### Description
The three pieces work in sequence:

1. **Internet access traffic forwarding** routes the user's web traffic through the GSA cloud service instead of straight out to the internet.
2. **TLS inspection** lets GSA decrypt HTTPS traffic at the service edge so policy engines can see what's inside. Without it, GSA only sees the destination (for example, "user is going to chatgpt.com"), rather than the file or URL path that actually matters for a DLP decision.
3. **Content policies** then inspect the decrypted payload and block or allow it accordingly.
### Example scenario
You're Adele, trying to upload a pricing file to an external AI service. The upload is blocked immediately because the system recognizes the data as confidential-before it ever leaves your environment.
### Success criteria
- TLS inspection enabled
- DLP policy active
- Upload attempts blocked
### Learning resources
- Network DLP in GSA

---

### Key steps

#### 01: Enable the internet access traffic forwarding profile

The internet access profile routes outbound web traffic on ports 80 and 443 through the GSA cloud service.

1. On the **@lab.VirtualMachine(Windows11).SelectLink** virtual machine, switch to your Microsoft Edge window.


1. Switch back to the tab with `entra.microsoft.com` open.


1. In the leftmost pane, go to **Global Secure Access** > **Connect** > **Traffic forwarding**.


1. Turn on **Internet access profile**.


1. In the dialog, select **Enable Microsoft and Internet Access profiles**.



	!IMAGE[al95tbim.png](../../media/al95tbim.png)

1. In the **Internet access profile** tile, under **User and group assignments**, select **View**.



	!IMAGE[8l8uprxj.png](../../media/8l8uprxj.png)

1. In the flyout pane:


1. Select **Assign to all users**.


1. In the dialog, select **OK**.


1. At the bottom of the pane, select **Done**.



===

#### 02: Generate a TLS inspection certificate

Transport Layer Security (TLS) inspection in Microsoft Entra Internet Access lets you decrypt and inspect encrypted traffic at service edge locations. This lets GSA apply advanced security controls like threat detection, granular web content filtering, and other content controls.

>[!knowledge] For more information, take a look at the [Key concepts](https://learn.microsoft.com/en-us/entra/global-secure-access/tutorial-internet-access-tls-inspection#key-concepts).

1. In the leftmost pane, go to **Global Secure Access** > **Secure** > **TLS inspection policies**.


1. At the top of the page, select the **TLS inspection settings** tab.


1. On the top bar, select **Create certificate**.



	!IMAGE[uif3czxn.png](../../media/uif3czxn.png)

1. In the flyout pane, enter the following:



	| Item | Value |
	|---|---|
	| Certificate name | `zavatls` |
	| Common name | `Zava TLS ICA` |
	| Organizational name | `Zava IT` |

	!IMAGE[30lmqvvv.png](../../media/30lmqvvv.png)

1. At the bottom of the pane, select **Create CSR**.


1. In the **Downloads** dialog, select the folder icon to go directly to the **Downloads** folder.



	!IMAGE[ruzm8xp2.png](../../media/ruzm8xp2.png)

1. Copy the **full** file name including **.csr**, and paste it in the following text box:



    @lab.TextBox(csr)

	!IMAGE[2iecsgjs.png](../../media/2iecsgjs.png)

    >[!alert] This value will be referenced again in the next step.

===

#### 03: Sign the CSR using the lab helper script

In production, customers could hand the .csr file to their enterprise PKI team, who would sign it with the corporate root CA. For the lab, a helper script at **C:\Lab Files\signGsaCert.ps1** creates a Zava root CA on the VM and signs the CSR with it.

>[!note] **OpenSSL prerequisite**
>
>This step uses **OpenSSL** to sign the certificate request generated by GSA, which has been pre-installed.

1. On the VM's taskbar, right-click the **Start** button, then select **Terminal (Admin)**.


1. In the dialog, select **Yes**.


1. In the terminal, run the following script:



	`& "C:\Lab Files\signGsaCert.ps1" -CSRPath "C:\Users\Admin\Downloads\@lab.Variable(csr)"`

	!IMAGE[i2017ma3.png](../../media/i2017ma3.png)

	>[!help] The message in the screenshot in red can be safely ignored. 
	>
	>**openssl.exe : Certificate request self-signature ok** 

	>[!alert] This command uses the file name you pasted in the prior step.

1. Confirm the following files are in your **Downloads** folder:



	- **signedcertificate.pem**
    - **rootCA.pem**

	!IMAGE[g0sfouw9.png](../../media/g0sfouw9.png)

===

#### 04: Upload the signed certificate and chain to GSA

1. Go back to your Microsoft Edge tab with the **TLS inspection settings** page open.


1. On the row for the **zavatls** certificate, under the **Status** column, select **Upload certificate**.



	!IMAGE[s96wi5tw.png](../../media/s96wi5tw.png)

1. In the flyout pane:


1. Under **Upload certificate**, select **Browse**.


1. Go to **Downloads**, select **signedcertificate.pem**, then select **Open**.



		!IMAGE[wx2m9g7c.png](../../media/wx2m9g7c.png)

1. Under **Upload chain**, select **Browse**.


1. In **Downloads**, select **rootCA.pem**, then select **Open**.


1. At the bottom of the pane, select **Upload signed certificate**.


1. On the row for the **zavatls** certificate, select the ellipsis (**...**), then select **Enable**.



	!IMAGE[br00dr15.png](../../media/br00dr15.png)

1. Wait until the **Status** changes to **Enabled** before proceeding.



	>[!alert] This may take a couple minutes. Periodically select **Refresh** on the top bar.

===

#### 05: Create a TLS inspection policy

1. At the top of the page, select the **TLS inspection policies** tab.


1. On the top bar, select **Create policy**.



	!IMAGE[6juim0u4.png](../../media/6juim0u4.png)

1. On the **Basics** tab, enter the following:



	| Item | Value |
	|---|---|
	| Name | `Zava TLS Inspection Policy` |
	| Description | `Default inspect policy for end-user internet traffic.` |
	| Default action | **Inspect** |

1. At the top of the page, select the **Review** tab.


1. At the bottom of the page, select **Submit**.



===

#### 06: Create a network DLP content policy

With internet access forwarding and TLS inspection in place, GSA can now see the actual content of web traffic. The content policy you'll create will define what content is blocked and where.

1. In the leftmost pane, go to **Global Secure Access** > **Secure** > **Content policies**.


1. On the top bar, select **Create policy**.



	!IMAGE[sdgs453d.png](../../media/sdgs453d.png)

1. On the **Basics** tab, enter the following:



	| Item | Value |
	|---|---|
	| Name | `Block uploads to ChatGPT` |
	| Description | `Blocks specific uploads to ChatGPT from managed devices to prevent shadow AI data exfiltration.` |

1. Select **Next**.


1. On the **Rules** tab, select **Add rule**.


1. On the **Add Content Rule** page, enter the following:



	| Item | Value |
	|---|---|
	| Rule name | `Block uploads to ChatGPT` |
	| Description | `Block rule for Word/PDF file uploads to ChatGPT endpoints.` |
	| Action | **Block** |
	| Activities | **Upload** |
	
	!IMAGE[70b5m631.png](../../media/70b5m631.png)

1. Select the **File content types** dropdown menu, then select the following:



	- **Word (97-2003)**
    - **Word Document**
    - **PDF**

	!IMAGE[09w8gqvg.png](../../media/09w8gqvg.png)

1. Under **Destinations**, select **Add destination** > **URL**.



	!IMAGE[x8zwbi2x.png](../../media/x8zwbi2x.png)

1. In the flyout pane:


1. Enter `https://chatgpt.com/backend-api/files`, then select **Add URL**.


1. Enter `https://chatgpt.com/backend-api/files/process_upload_stream`, then select **Add URL**.



		!IMAGE[mep4zv00.png](../../media/mep4zv00.png)

1. At the bottom of the pane, select **Add**.


1. Under **Destinations**, select **Add destination** > **FQDN**.



	!IMAGE[ugo4t4ei.png](../../media/ugo4t4ei.png)

1. In the flyout pane:


1. Enter `*.oaiusercontent.com`, then select **Add FQDN**.


1. At the bottom of the pane, select **Add**.



	>[!note] These are the endpoints ChatGPT uses for file upload operations, identified using browser developer tools.

1. At the bottom of the page, select **Add**.



	!IMAGE[nscaxigk.png](../../media/nscaxigk.png)

1. Select **Next**.


1. Select **Create**.



===

#### 07: Create the security profile and link the policies

Security profiles group one or more policies together, which you can then apply to user traffic via Conditional Access. You'll create a security profile and link the TLS inspection and content policies to it.

1. In the leftmost pane, go to **Global Secure Access** > **Secure** > **Security profiles**.


1. On the top bar, select **Create profile**.



	!IMAGE[efit0ioc.png](../../media/efit0ioc.png)

1. On the **Basics** tab, enter the following:



	| Item | Value |
	|---|---|
	| Profile name | `Zava Internet Security` |
	| Description | `End-user internet security profile: TLS inspection, network DLP, prompt injection protection.` |

1. Select **Next**.


1. Select **Link a policy** > **Existing TLS inspection policies**.



	!IMAGE[2lxjbz0w.png](../../media/2lxjbz0w.png)

1. In the flyout pane:


1. For **Policy name**, select **Zava TLS Inspection Policy**.


1. At the bottom of the pane, select **Add**.


1. Select **Link a policy** > **Existing content policy**.



	!IMAGE[j5ax98xu.png](../../media/j5ax98xu.png)

1. In the flyout pane:


1. From the **Policy name** dropdown menu, select **Block uploads to ChatGPT**.


1. At the bottom of the pane, select **Add**.


1. Select **Next**.


1. Select **Create a profile**.



	!IMAGE[xplqcn70.png](../../media/xplqcn70.png)

===

#### 08: Assign the security profile via Conditional Access

You'll now tie the security profile to a new Conditional Access policy.

1. In the leftmost pane, go to **Entra ID** > **Conditional Access**.


1. On the top bar, select **Create new policy**.


1. In the **Name** box, enter:



	`CA03 - Zava Internet Security Profile`

1. Under **Users or agents**, select **0 users or agents selected**.


1. Under **Include**, select **All users**.



		!IMAGE[5vtgvmxp.png](../../media/5vtgvmxp.png)

1. Select the **Exclude** tab.


1. Select the **Users and groups** checkbox.


1. Enter and select `@lab.CloudCredential(WWLM365Enterprise2019wSPE_EStakeholderKimFrank).AdministrativeUsername`.


1. At the bottom of the pane, choose **Select**.



	!IMAGE[8fbqqf97.png](../../media/8fbqqf97.png)

1. Under **Target resources**, select **No target resources selected**.


1. Under **Include**, select **All internet resources with Global Secure Access**.



		!IMAGE[40hao6r9.png](../../media/40hao6r9.png)

1. Under **Session**, select **0 controls selected**.


1. In the flyout pane, select **Use Global Secure Access security profile**.


1. In the dropdown menu, select **Zava Internet Security**.



		!IMAGE[rpz2n4eb.png](../../media/rpz2n4eb.png)

1. At the bottom of the pane, choose **Select**.


1. Set **Enable policy** to **On**.



	!IMAGE[ralxupaa.png](../../media/ralxupaa.png)

1. At the bottom of the page, select **Create**.



===

## Task 02: Govern Copilot Studio agents with GSA
### Introduction
In this task, you'll bring Copilot Studio agent traffic under GSA, then apply a web content filtering policy that governs where those agents can connect.
### Description
Two GSA capabilities address this:
- **MCP traffic logging** gives security teams visibility into what MCP servers agents are calling, which tools those servers expose, and what arguments are passed.
- **Secure Web and AI Gateway for Copilot Studio agents** brings the outbound network traffic of Copilot Studio agents under the same GSA policy engine used for end-user traffic - web content filtering, threat intelligence filtering, content policy, and more.
### Example scenario
You're Adele, relying on internal AI agents. Every action those agents take is monitored and governed, ensuring they only access approved resources.
### Success criteria
- Agent traffic routed through GSA
- Policies applied to AI activity
- Traffic visible to administrators
### Learning resources
- GSA for AI agents

---

### Key steps

#### 01: Learn about Gen AI Insights logs

GSA Model Context Protocol (MCP) logging provides advanced monitoring and analysis capabilities for MCP traffic between client MCP on devices and remote MCP servers. This provides visibility into which MCP servers are being used, what tools and resources they expose, and how those tools are invoked. 

MCP logging helps you discover shadow MCP servers, enforce security and governance controls on AI agent communications, and understand which tools are being exposed and used. It also monitors a client MCP that is used by the Copilot Studio agent and a remote MCP server if you've enabled GSA MCP integration for Copilot Studio agents.

MCP logging uses deep packet inspection to identify MCP traffic based on the protocol itself, rather than a predefined cloud app catalog. This approach enables discovery of previously unknown or private MCP servers that employees might be using.

>[!knowledge] For more information, visit [MCP traffic logs](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-view-model-context-protocol-logging).

===

#### 02: Enable Global Secure Access for Copilot Studio agents

By default, Copilot Studio agents make outbound network calls directly to the internet, bypassing your GSA policies entirely. You'll enable an integration in the Power Platform admin center that routes agent traffic through GSA, bringing every agent connection under the same network security plane as your users.

1. Open a new browser tab, then go to `admin.powerplatform.microsoft.com`.


1. If prompted, select your lab admin account.


1. In the leftmost pane, go to **Security**.


1. In the page's menu, select **Identity & access**.



	!IMAGE[c13hfln3.png](../../media/c13hfln3.png)

1. Select **Global Secure Access for Agents**.



	!IMAGE[dh6cgign.png](../../media/dh6cgign.png)

1. In the flyout pane:


1. Select the pre-deployed **Dev One** environment.


1. At the bottom of the pane, select **Set up**.



		!IMAGE[rcynowb1.png](../../media/rcynowb1.png)

1. Turn on **Enable Global Secure Access for Agents**.



		!IMAGE[hc3x7yl2.png](../../media/hc3x7yl2.png)

1. At the bottom of the pane, select **Save**.



	>[!knowledge] After enabling this integration, pre-existing Copilot Studio custom connectors must be edited and saved again before their traffic will route through GSA. Connectors created after the integration is enabled will use it automatically.

===

#### 03: Create a web content filtering policy

You'll start by creating a web content filtering policy that blocks high-risk categories.

1. Switch back to your `entra.microsoft.com` tab.


1. In the leftmost pane, go to **Global Secure Access** > **Secure** > **Web content filtering policies**.


1. On the top bar, select **Create policy**.



	!IMAGE[pscz0ekw.png](../../media/pscz0ekw.png)

1. On the **Basics** tab, enter the following:



	| Item | Value |
	|---|---|
	| Name | `Zava Agent Web Filtering` |
	| Description | `Blocks high-risk web categories from Copilot Studio agent traffic.` |
	| Action | **Block** |

1. Select **Next**.


1. On the **Policy Rules** tab, select **Add Rule**.


1. In the flyout pane:


1. Enter the following:



        | Item | Value |
        |---|---|
        | Name | `Block high-risk categories` |
        | Destination type | **webCategory** |

		!IMAGE[tnsp1mk3.png](../../media/tnsp1mk3.png)

1. Under **Search**, enter and select the following:



		- `Hacking`
        - `Illegal Software`
        - `Web Repository And Storage`

		>[!knowledge] You can build out the full set of categories appropriate to your organization's risk tolerance and compliance posture for AI agent egress.

1. At the bottom of the pane, select **Add**.



		!IMAGE[ste8wnsd.png](../../media/ste8wnsd.png)

1. Select **Next**.


1. Select **Create policy**.



	!IMAGE[k3do4lju.png](../../media/k3do4lju.png)

===

#### 04: Apply the web content filtering policy to the baseline profile

Copilot Studio agents make outbound calls without a user sign-in, so Conditional Access policies don't apply. Security policies for agents are instead linked to the baseline profile, which applies tenant-wide to all agent traffic.

1. In the leftmost pane, go to **Global Secure Access** > **Secure** > **Security profiles**.


1. At the top of the page, select the **Baseline profile** tab.



	!IMAGE[hkuhcejk.png](../../media/hkuhcejk.png)

1. Below the tabs, select **Edit profile**.



	!IMAGE[0uyv0jef.png](../../media/0uyv0jef.png)

1. In the page's menu, select **Link policies**.


1. Select **Link a policy** > **Existing web filtering policy**.



	!IMAGE[fblnx3o5.png](../../media/fblnx3o5.png)

1. In the flyout pane:


1. For **Policy name**, select **Zava Agent Web Filtering**.


1. At the bottom of the pane, select **Add**.



	>[!knowledge] Combined with MCP traffic visibility, you have both detection (Gen AI Insights) and enforcement (baseline profile policy) for AI agent egress.

===

## Task 03: Block prompt injection attacks at the network layer
### Introduction
In this task, you'll create a prompt policy that scans outbound LLM requests for adversarial patterns (jailbreak attempts, instruction overrides, exfiltration prompts) and blocks them at the network layer before they reach the model.
### Description
Prompt injection attacks are the top OWASP-listed risk for LLM applications. An attacker crafts input designed to make the model ignore its system instructions, reveal sensitive data, perform unintended actions, or generate harmful content. Traditional application-layer defenses (input sanitization, prompt guards built into the app) could be bypassed and require code changes to update.
### Example scenario
You're Adele, pasting external content into an internal AI assistant. Hidden malicious instructions attempt to manipulate the response-but the system detects and blocks them before they reach the model.
### Success criteria
- Prompt policy active
- Adversarial prompts blocked
- Events logged for monitoring
### Learning resources
- Prompt injection protection

---

### Key steps

#### 01: Create the prompt policy

1. In the leftmost pane, go to **Global Secure Access** > **Secure** > **Prompt policies**.


1. On the top bar, select **Create policy**.



	!IMAGE[klbaeifa.png](../../media/klbaeifa.png)

1. On the **Basics** tab, enter the following:



	| Item | Value |
	|---|---|
	| Name | `Zava Prompt Injection Protection` |
	| Description | `Blocks adversarial prompts to enterprise LLM endpoints from user devices.` |

1. Select **Next**.


1. On the **Rules** tab, select **Add rule**.


1. On the **Prompt Rule** page, enter the following:



	| Item | Value |
	|---|---|
	| Rule name | `Block adversarial prompts` |
	| Description | `Block rule for prompt injection / jailbreak patterns.` |
	| Action | **Block** |

	!IMAGE[107ugikt.png](../../media/107ugikt.png)

1. Under **Add conversation scheme**, select **Conversation scheme**.



	!IMAGE[77ictryp.png](../../media/77ictryp.png)

1. In the flyout pane:


1. From the **Type** dropdown menu, select **ChatGPT**.



		!IMAGE[j2gra6at.png](../../media/j2gra6at.png)

1. Select **Add**.



	>[!knowledge] 
	>For custom LLMs, you'd select **Custom** and provide the endpoint URL and JSON path that points to where the prompt lives in the request body.

1. Repeat the steps to add additional conversation schemes for the following LLMs:



	- **Claude**
	- **Gemini**

	>[!note] You can add as many schemes as you need. Each one expands the coverage of the prompt policy to another LLM provider.

1. At the bottom of the page, select **Add**.



	!IMAGE[zax6yvio.png](../../media/zax6yvio.png)

1. Select **Next**.


1. Select **Create**.



===

#### 02: Link the prompt policy to the Zava Internet Security profile

You'll now attach the policy to the **Zava Internet Security** profile so it becomes part of the same Conditional Access-gated stack.

1. In the leftmost pane, go to **Global Secure Access** > **Secure** > **Security profiles**.


1. Select **Zava Internet Security**.


1. In the page's menu, select **Link policies**.


1. Select **Link a policy** > **Existing prompt policy**.



	!IMAGE[jyrtmwxz.png](../../media/jyrtmwxz.png)

1. In the flyout pane:


1. For **Policy name**, select **Zava Prompt Injection Protection**.


1. At the bottom of the pane, select **Add**.


1. Observe the profile now shows three linked policies:



	- **Zava TLS Inspection Policy**
	- **Block uploads to ChatGPT**
	- **Zava Prompt Injection Protection**

	!IMAGE[1liyj9cg.png](../../media/1liyj9cg.png)

	>[!note] When **CA03** evaluates an end user's request to any internet resource, all three policies fire in sequence.

---

AI access now flows through the same policy engine that gates Adele's identity and the Finance Portal. Shadow AI exfiltration, MCP-speaking agents, and prompt injection are all visible and enforceable at the network layer, without requiring code changes to any application.

===

>[!Alert] **IMPORTANT:** These labs are hosted on the Skillable platform. Completion data is collected and then exported to Success Factors every Monday. SF require another 1-3 days to process that data. The status for this lab will be visible in Viva and Learning Path next week. 
>
Be sure to select "**Submit**" in the bottom right corner to get credit for completing this lab. 

@lab.ActivityGroup(completionsurvey)

>[!Alert] After answering the survey questions, select **submit** to complete and end the lab. **This is required in order to receive credit for lab completion**.

# Congratulations!

You've completed the lab.

Select **End** to mark the lab as **Complete**.

