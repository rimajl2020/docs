---
title: Adding organizations to your enterprise
intro: 'Learn how to add organizations to your enterprise using three different methods.'
redirect_from:
  - /github/setting-up-and-managing-your-enterprise/managing-organizations-in-your-enterprise-account/adding-organizations-to-your-enterprise-account
  - /articles/adding-organizations-to-your-enterprise-account
  - /github/setting-up-and-managing-your-enterprise-account/adding-organizations-to-your-enterprise-account
  - /github/setting-up-and-managing-your-enterprise/adding-organizations-to-your-enterprise-account
  - /admin/user-management/managing-organizations-in-your-enterprise/adding-organizations-to-your-enterprise
versions:
  ghec: '*'
type: how_to
topics:
  - Administrator
  - Enterprise
  - Organizations
shortTitle: Add organizations
permissions: Enterprise owners
---

There are three ways to add organizations to your enterprise.

* **Create** a new organization in your enterprise.
* **Invite** an existing organization to join your enterprise.
* **Transfer** an existing organization between enterprise accounts on {% data variables.product.prodname_dotcom_the_website %}.

{% data reusables.enterprise.create-an-enterprise-account %} See [AUTOTITLE](/admin/managing-your-enterprise-account/creating-an-enterprise-account).

## Limitations

If you use {% data variables.enterprise.data_residency %}, you cannot transfer organizations between {% data variables.product.prodname_dotcom_the_website %} and your enterprise on {% data variables.enterprise.data_residency_site %}. Instead, you must migrate organizations with the {% data variables.product.prodname_importer_proper_name %}. See [AUTOTITLE](/migrations/using-github-enterprise-importer/migrating-between-github-products/about-migrations-between-github-products).

If you use {% data variables.product.prodname_emus %}, the following limitations apply:

* Adding existing organizations to your enterprise is not possible.
* Existing organizations from an enterprise with managed users cannot be added to a different enterprise.

## Changes when adding an existing organization

After you add an existing organization to your enterprise, the organization's resources remain accessible to members at the same URLs, and the following changes will apply.

* **Two-factor authentication (2FA):** If required by the enterprise, members without 2FA, or with insecure 2FA, will be unable to access organization resources until they configure 2FA that meets the enterprise's 2FA security requirements.
* **Enterprise licenses:** Members become part of the enterprise, and usage is billed to the enterprise account. You must ensure that the enterprise account has enough licenses to accommodate any new members. See [AUTOTITLE](/billing/managing-your-billing/about-billing-for-your-enterprise).
* **Enterprise role management:** Enterprise owners can manage their roles within the organization. See [AUTOTITLE](/admin/user-management/managing-organizations-in-your-enterprise/managing-your-role-in-an-organization-owned-by-your-enterprise).
* **Enterprise policies:** Any policies applied to the enterprise will apply to the organization. {% data reusables.actions.org-to-enterprise-actions-permissions %}

* **SAML SSO Configuration:**

  * If SAML SSO is configured **for the destination enterprise**, the enterprise's SAML configuration will apply to the organization.
    * If SAML is currently configured on the organization, the enterprise account's SAML configuration will override the organization's configuration. SCIM is not available at the enterprise level for enterprises that use personal accounts, so SCIM will be disabled for the organization. The new inherited enterprise SAML settings will be displayed on the organization's SAML settings page.
    * If SAML is ever disabled for the enterprise, the organization SAML settings will revert back to their original configuration.
  * If SAML is **not** configured for the destination enterprise, the organization will retain any existing SAML and SCIM settings.
  * If organization members have existing SAML authorizations for {% data variables.product.pat_generic_plural %} or SSH keys to access the organization, these authorizations will remain active.
    * To see these authorizations, SAML must be configured for either the organization or enterprise, and the user must have a linked SAML identity.
    * To access additional organizations owned by the enterprise, members must authorize the {% data variables.product.pat_generic %} or key. See [AUTOTITLE](/authentication/authenticating-with-saml-single-sign-on/authorizing-a-personal-access-token-for-use-with-saml-single-sign-on) and [AUTOTITLE](/authentication/authenticating-with-saml-single-sign-on/authorizing-an-ssh-key-for-use-with-saml-single-sign-on).

* **Trial enterprise:** Certain features may be disabled if added to a trial enterprise. See [AUTOTITLE](/admin/overview/setting-up-a-trial-of-github-enterprise-cloud#features-not-included-in-the-trial).
* **{% data variables.product.prodname_github_connect %}:** If the organization was connected to {% data variables.product.prodname_ghe_server %} using {% data variables.product.prodname_github_connect %}, adding the organization to an enterprise will not update the connection. {% data variables.product.prodname_github_connect %} features will no longer function for the organization. To continue using {% data variables.product.prodname_github_connect %}, you must disable and re-enable the feature. See [AUTOTITLE](/enterprise-server@latest/admin/configuration/configuring-github-connect/managing-github-connect) in the {% data variables.product.prodname_ghe_server %} documentation.
* **{% data variables.product.prodname_marketplace %} apps:** If you add a standalone organization that uses billed {% data variables.product.prodname_marketplace %} apps, the organization can continue to use the apps, but usage will be billable to the enterprise.
  * If your enterprise is billed via invoice, contact the app vendor and pay directly.
  * If your enterprise is billed via credit card or PayPal, billing continues automatically.
  To transfer an existing organization with billed apps between enterprise accounts, first remove the billed apps and then re-add the apps after the transfer is complete.
* **Sponsorships:** Any sponsorships by the organization will be canceled.
* **Coupons:** Any coupons will be removed from the organization. To reapply the coupon, [contact our sales team](https://github.com/enterprise/contact).

## Handling {% data variables.product.prodname_sponsors %} with Azure billing

If your organization is added to an enterprise account with Azure metered billing, any active {% data variables.product.prodname_sponsors %} sponsorships will be canceled. While your organization remains under enterprise billing through Azure, you will not be able to reactivate these sponsorships, as sponsoring is not currently supported for organizations billed through Azure.

To continue using {% data variables.product.prodname_sponsors %}, create a new, separate "shell" organization that is not linked to your enterprise account or Azure billing. You can use this shell organization to manage sponsorships independently.

> [!NOTE]
> After you create a shell organization, update any public references or documentation to point sponsors to the new organization.

## Creating a new organization

New organizations you create within your enterprise account settings are included in your enterprise account's {% data variables.product.prodname_ghe_cloud %} subscription.

Enterprise owners who create an organization owned by the enterprise account automatically become organization owners. See [AUTOTITLE](/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization).

During a trial of {% data variables.product.prodname_ghe_cloud %}, you can create up to three new organizations in your enterprise.

{% data reusables.enterprise-accounts.access-enterprise %}
{%- ifversion enterprise-readme %}
1. In the left sidebar, click **Organizations**.
{%- endif %}
1. Above the list of organizations, click **New organization**.
1. Under "Organization name," type a name for your organization.
1. Click **Create organization**.
1. Optionally, under "Invite owners," type the username of a person you'd like to invite to become an organization owner, then click **Invite**.
1. Click **Finish**.

## Inviting an existing organization

Enterprise owners can invite existing organizations to join their enterprise account.

During a trial of {% data variables.product.prodname_ghe_cloud %}, you can invite organizations to join your trial enterprise. You can invite organizations that are not currently owned by another enterprise. If an organization you want to invite is already owned by another enterprise, you cannot invite it to your trial enterprise.

After you invite the organization, and before an owner approves the invitation, you can cancel or resend the invitation at any time.

{% data reusables.enterprise-accounts.access-enterprise %}
{%- ifversion enterprise-readme %}
{% data reusables.enterprise-accounts.click-organizations-tab %}
{%- endif %}
1. Above the list of organizations, click **Invite organization**.
1. Under "Organization name," start typing the name of the organization you want to invite and select it when it appears in the dropdown list.
1. Click **Invite organization**. The organization owners will receive an email inviting them to join the enterprise.
1. After an organization owner has approved the invitation, navigate back to the **Organizations** tab of the enterprise settings.
1. Under "Organizations," click **X pending**.
1. To complete the transfer, next to the organization name, click **Approve**.

## Transferring an existing organization

Enterprise owners can transfer existing organizations between enterprise accounts. You must be an enterprise owner of both enterprise accounts.

You cannot transfer an existing organization to or from an {% data variables.enterprise.prodname_emu_enterprise %} or an enterprise account that is currently enrolled in a trial of {% data variables.product.prodname_ghe_cloud %}.

If the existing organization uses billed apps, make sure to remove the billed apps before transferring. After the transfer is complete, re-add the apps.

{% data reusables.enterprise-accounts.access-enterprise %}
{%- ifversion enterprise-readme %}
{% data reusables.enterprise-accounts.click-organizations-tab %}
{%- endif %}
1. Next to the organization you want to transfer, select the {% octicon "kebab-horizontal" width="16" aria-label="Organization settings" %} dropdown menu, then click **Transfer organization**.

   ![Screenshot of the expanded dropdown menu labeled with the kebab icon, for an organization. The "Transfer organization" option is outlined.](/assets/images/help/business-accounts/transfer-organization.png)

1. Select the **Select enterprise** dropdown menu, start typing the name of the destination enterprise, and click the enterprise you want to transfer the organization to.
1. Click **Review transfer**.
1. To confirm the transfer, click **Transfer organization**.
