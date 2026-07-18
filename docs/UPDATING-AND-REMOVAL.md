# Update, disable, or remove

## Update the package

1. Download the new `.sppkg` and checksum from GitHub Releases.
2. Verify the checksum.
3. Upload the new package to **Apps for SharePoint** and replace the existing file.
4. Review new or changed API permission requests.
5. Confirm tenant-wide deployment.
6. Test with a manager and ordinary user on desktop and mobile.

## Roll back

1. Upload the previously retained `.sppkg` to **Apps for SharePoint** and replace the current package.
2. Verify the tenant-wide extension registration and API access.

## Disable without uninstalling

Open **Tenant Wide Extensions** on the App Catalog site and set the registration to disabled. This is the fastest reversible way to stop the menu from rendering.

## Remove

1. Disable or delete the Tenant Wide Extensions entry.
2. Remove the app from **Apps for SharePoint** when it is no longer needed.
3. Review and revoke API permissions that are no longer required.
