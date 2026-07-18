# Installation and tenant-wide activation

This guide is for SharePoint and Microsoft 365 administrators evaluating Tenant Wide Mega Menu.

## Prerequisites

- SharePoint Online tenant with a tenant App Catalog.
- Permission to upload and deploy SharePoint Framework packages.
- Permission to review and approve SharePoint API access requests.
- A modern SharePoint test page.
- An account that is a Global Administrator, SharePoint Administrator, or a member of a planned menu-manager group.
- Appropriate SharePoint access to the tenant App Catalog site.

Start in a test tenant or controlled pilot group whenever possible.

## 1. Download and verify the package

Download these files from the [latest GitHub release](https://github.com/joaojmendes/tenant-wide-mega-menu/releases/latest):

- `sharepoint-mega-menu.sppkg`
- `sharepoint-mega-menu.sppkg.sha256`

Optional checksum verification:

### PowerShell

```powershell
Get-FileHash .\sharepoint-mega-menu.sppkg -Algorithm SHA256
```

### macOS or Linux

```bash
shasum -a 256 sharepoint-mega-menu.sppkg
```

Compare the result with the value in the `.sha256` file.

## 2. Upload to the tenant App Catalog

1. Open the tenant App Catalog site.
2. Open **Apps for SharePoint**.
3. Upload `sharepoint-mega-menu.sppkg`.
4. Review the package name, version, requested permissions, and deployment scope.
5. Select **Enable this app and add it to all sites**.
6. Select **Enable app** or **Deploy**, depending on the current SharePoint interface.

The package uses tenant-wide deployment and includes its client-side assets. Initial activation can require several minutes to propagate.

## 3. Approve API access

1. Open the **SharePoint Admin Center**.
2. Open **Advanced** > **API access**.
3. Review the pending requests created by the package.
4. Approve the requests required by your test plan:

| Resource | Permission |
| --- | --- |
| Microsoft Graph | `GroupMember.Read.All` |
| License-manager-auth | `user_impersonation` |

Without Microsoft Graph consent, group search, audience targeting, or configured editor-group checks may fail. Without the license-service permission, product entitlement validation may fail.

## 4. Verify the tenant-wide extension registration

Open **Site contents** on the tenant App Catalog site, then open **Tenant Wide Extensions**.

Verify that an enabled entry exists with:

| Field | Value |
| --- | --- |
| Component ID | `a29898f5-586e-4c89-a187-70e0533bcac5` |
| Location | `ClientSideExtension.ApplicationCustomizer` |
| Disabled | No |

If SharePoint did not create it automatically, create the entry manually with those values. Leave web and list template restrictions empty for broad tenant activation.

## 5. Configure the component properties

Edit the **Component Properties** value in **Tenant Wide Extensions**. Use valid JSON:

```json
{
  "title": "Contoso",
  "configurationEditorsGroupIds": [
    "11111111-1111-1111-1111-111111111111"
  ]
}
```

Replace:

- `Contoso` with the initial company or menu title;
- the sample GUID with the Microsoft Entra **object ID** of your manager group.

Multiple groups are supported. Do not use group names, email addresses, SharePoint group IDs, application IDs, or tenant IDs.

The package installs with an empty manager-group list. Global Administrators and SharePoint Administrators remain authorized to perform the first configuration.

## 6. Provision the shared configuration

1. Open a modern SharePoint page where the extension is active.
2. If prompted, complete the product test-license or entitlement flow.
3. Select the **Settings** action in the menu.
4. Configure at least one menu item and select **Save menu**.

## 7. Validate the deployment

Test at minimum:

1. Manager sees **Settings** and can save.
2. Ordinary user does not see **Settings**.
3. Both users see and can launch **Company Tools**.
4. Only the manager sees the tool-management control.
5. Desktop, overflow, and mobile layouts work.
6. Audience-targeted entries are visible only to intended users.
7. Menu links and images are accessible from more than one SharePoint site.
8. Refreshing and SharePoint single-page navigation preserve the menu.

Continue with the [configuration guide](CONFIGURATION.md).
