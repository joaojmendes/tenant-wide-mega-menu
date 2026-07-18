# Troubleshooting

Before opening an issue, confirm the package version, browser version, tenant-wide registration, API approvals, and current user's authorization.

## The menu does not appear

1. Confirm the package is deployed and enabled in **Apps for SharePoint**.
2. Confirm **Tenant Wide Extensions** has an enabled entry for component ID `a29898f5-586e-4c89-a187-70e0533bcac5`.
3. Confirm the location is `ClientSideExtension.ApplicationCustomizer`.
4. Validate the Component Properties JSON.
5. Test a modern SharePoint page with a top placeholder.
6. Allow time for tenant-wide deployment propagation.
7. Check the browser console for bundle, entitlement, or configuration errors.

The menu intentionally does not render in an iframe or SharePoint embedded mode.

## The menu appears but is empty

- An empty menu is expected before the first successful save.
- Open Settings as a manager, add an item, and save.
- Look for `SharePointMegaMenu: failed to load menu configuration.` in the console.

## Settings is missing

- Confirm the user is a Global Administrator, SharePoint Administrator, or member of a configured editor group.
- Confirm `configurationEditorsGroupIds` contains Entra object IDs in valid JSON.
- Approve the requested Microsoft Graph permission.
- Sign out and in after changing roles or group membership.
- Verify the `/me/checkMemberGroups` request in browser developer tools.

## Settings opens but save fails

- Confirm the current user is an authorized manager.
- Confirm all requested API permissions are approved.
- Check the browser console and network panel for sanitized error details.
- Retry in a private browser window to rule out stale session data.

## Company Tools is empty

- Tools must be created by an authorized manager using the management gear.
- Confirm the latest configuration save completed.

## The tool-management gear is missing

The gear is intentionally restricted to authorized menu managers. Verify the same authorization and permissions used for Settings.

## Group search or audience targeting fails

- Confirm `GroupMember.Read.All` was approved in SharePoint Admin Center API access.
- Confirm the group is a Microsoft Entra group and the configured value is its object ID.
- Test with a direct object ID if display-name search returns no results.
- Remove and re-add recent group memberships, then sign out and in if tokens are stale.

When membership resolution fails, targeted entries are hidden by design.

## License or entitlement validation fails

- Confirm `License-manager-auth / user_impersonation` was approved.
- Confirm the browser can reach `license.spteckapps.com` and `licenses-api.spteckapps.com`.
- Check whether a proxy, firewall, Conditional Access policy, or browser extension blocks the request.
- Complete the trial or entitlement flow with the same tenant and user used for testing.

Do not post license tokens or tenant-sensitive entitlement data in a public issue.

## Images do not display

- Open the image URL as an ordinary target user.
- Confirm the file still exists and has not moved.
- Confirm the image format is supported.
- Prefer stable SharePoint URLs with tenant-wide read access.
- Check network and browser security errors.

## A top-level URL does not navigate

An item containing panel content is treated as a panel trigger. Put the destination in a direct link or footer button, or remove the panel content to make the item navigate directly.

## A saved change disappears

- Wait for the save to complete before navigating away.
- Check the browser console for a failed save.
- Confirm another manager did not overwrite the complete configuration with an older draft.

## Collect safe diagnostic information

Include:

- package version;
- browser and operating system;
- whether the user is a manager or ordinary user;
- sanitized Component Properties JSON;
- exact reproduction steps;
- expected and actual behavior;
- sanitized console errors and screenshots.

Never include access tokens, cookies, passwords, tenant secrets, license tokens, personal data, or confidential URLs.
