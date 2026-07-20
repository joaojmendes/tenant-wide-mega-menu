# Tenant Wide Mega Menu for SharePoint Online

Tenant Wide Mega Menu is a SharePoint Framework Application Customizer that adds shared, responsive navigation to modern SharePoint Online pages.

> This is a binary distribution and support repository. The source code is not published here. Use GitHub Issues to report test results, installation problems, and product defects.

[Download the latest]([https://github.com/joaojmendes/tenant-wide-mega-menu/releases/latest/download/sharepoint-mega-menu.sppkg](https://github.com/joaojmendes/tenant-wide-mega-menu/blob/main/sharepoint-mega-menu.sppkg)) · [Installation guide](docs/INSTALLATION.md) · [Configuration guide](docs/CONFIGURATION.md) · [Report a problem](https://github.com/joaojmendes/tenant-wide-mega-menu/issues/new/choose)

## What it provides

- One menu configuration shared across the SharePoint tenant.
- Responsive desktop, overflow, and mobile navigation.
- Direct links and multi-section mega-menu panels.
- Icons, images, descriptions, badges, featured content, and footer actions.
- Audience targeting with Microsoft Entra groups.
- Fixed **Tools** and **Settings** actions.
- A Company Tools launcher available to all users.
- Tool creation, editing, deletion, and ordering restricted to authorized managers.
- English and Portuguese administration labels.
- Automatic adaptation to the active SharePoint theme.

## Supported environment

- SharePoint Online.
- Modern SharePoint pages with the top application placeholder.
- A tenant App Catalog.
- Current Microsoft Edge, Google Chrome, or another current Chromium-based browser.

This package is not intended for SharePoint Server or classic SharePoint pages.

## Quick start

1. Download `sharepoint-mega-menu.sppkg`,  [here]([https://github.com/joaojmendes/tenant-wide-mega-menu/blob/main/sharepoint-mega-menu.sppkg).
2. Upload it to **Apps for SharePoint** in the tenant App Catalog.
3. Select **Enable this app and add it to all sites**, then deploy it.
4. Approve the requested API permissions in the SharePoint Admin Center.
5. Configure the tenant-wide extension properties for your company and manager groups.
6. Open a modern SharePoint page as a Global Administrator, SharePoint Administrator, or configured manager.
7. Use **Settings** to create and save the shared menu.

Read the complete [installation guide](docs/INSTALLATION.md) before deploying to a production tenant.

## Package identity

| Property | Value |
| --- | --- |
| Product | Tenant Wide Mega Menu |
| Current test release | `1.1.1` |
| Solution ID | `c4dc3ce1-9eee-45b1-94d1-a253b5d3a636` |
| Application Customizer ID | `a29898f5-586e-4c89-a187-70e0533bcac5` |
| Location | `ClientSideExtension.ApplicationCustomizer` |
| Deployment | Tenant-wide |

## Required API permissions

The package requests:

| Resource | Permission | Purpose |
| --- | --- | --- |
| Microsoft Graph | `GroupMember.Read.All` | Manager group checks, audience membership, and group search. |
| License-manager-auth | `user_impersonation` | Product entitlement and test-license validation. |

Review and approve these requests according to your organization's security and consent policies.

## Administration model

All users can see and launch configured menu entries and tools, subject to audience targeting. Management is available only to:

- Microsoft Entra Global Administrators;
- Microsoft Entra SharePoint Administrators; or
- members of the Entra groups configured in `configurationEditorsGroupIds` in the extension Properties via Tenant-Wide Extensions list.

## Testing and feedback

Please test with both a manager and an ordinary user. Include desktop and mobile widths, audience-targeted entries, tools, navigation, images, and permission boundaries.

Before reporting an issue:

- remove tenant names, user identities, tokens, license data, and confidential URLs;
- record the package version and browser version;
- include reproducible steps and the expected versus actual result;
- include sanitized console errors or screenshots when useful.

Use the [issue forms](https://github.com/joaojmendes/tenant-wide-mega-menu/issues/new/choose) so reports contain the information needed for investigation.

## Documentation

- [Install and activate](docs/INSTALLATION.md)
- [Configure and manage](docs/CONFIGURATION.md)
- [Troubleshoot](docs/TROUBLESHOOTING.md)
- [Update or remove](docs/UPDATING-AND-REMOVAL.md)
- [Support policy](SUPPORT.md)
- [Security reporting](SECURITY.md)
- [Release history](CHANGELOG.md)
- [Binary distribution notice](BINARY-LICENSE.md)

## Source code and licensing

This repository intentionally does not contain the application source code. The downloadable `.sppkg` contains compiled assets required by SharePoint Online. Availability of the package on GitHub does not make the product open source.

See [BINARY-LICENSE.md](BINARY-LICENSE.md) before downloading or installing the package.
