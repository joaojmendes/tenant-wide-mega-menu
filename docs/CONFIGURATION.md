# Configuration and administration

Tenant Wide Mega Menu uses one shared configuration for the entire tenant. A save from any site updates the menu everywhere the extension is active.

## Who can manage the menu

Management is available to:

- Global Administrators;
- SharePoint Administrators; or
- members of an Entra group listed in `configurationEditorsGroupIds`.

## Open the editor

1. Open a modern SharePoint page where the menu is visible.
2. Select the **Settings** gear on the right side of the menu.
3. Edit the menu.
4. Select **Save menu** and wait for the save to complete.

## Menu identity

Configure the title and an icon or image displayed at the left side of the menu.

- A saved title overrides the extension's `title` property.
- A saved image takes precedence over an icon.
- Images must be readable by users on every site where the menu appears.
- Add alternative text for informative images; use empty alternative text for decorative images.

## Menu behavior

| Setting | Default | Description |
| --- | --- | --- |
| Panel width | `820` | Desktop mega-menu panel width. |
| Mobile breakpoint | `760` | Width at which the mobile navigation replaces desktop navigation. |
| Overflow label | `More` | Label for desktop items that do not fit. |
| Mobile label | `Open` | Accessible label for opening mobile navigation. |
| Close mobile label | `Close` | Accessible label for closing mobile navigation. |

## Actions

Actions appear on the right side of the menu. Custom actions support text, description, icon, appearance, shape, icon-only display, availability, audience targeting, and a navigation target.

Two actions are required:

- **Tools** is visible to all users and opens Company Tools.
- **Settings** is visible only to authorized managers and opens the editor.

Required actions cannot be removed or hidden.

## Company Tools

All users can open and launch configured tools. Only authorized managers can create, edit, delete, or reorder them.

To manage tools:

1. Open **Company Tools**.
2. Select the management gear. It appears only for an authorized manager.
3. Add or edit the tool title, description, navigation URL, icon or image, color, and new-tab behavior.
4. Reorder tools as required.
5. Save the tool changes.

Tool URLs and images use the same safe-URL validation as the menu. Supported navigation schemes include HTTP, HTTPS, `mailto`, `tel`, and relative URLs.

## Top-level menu items

A top-level item can be:

- a direct navigation link; or
- a trigger for a mega-menu panel containing direct links, sections, featured content, footer text, or footer buttons.

When an item has panel content, selecting it opens the panel instead of navigating to the item's own URL.

Keep item keys unique and stable.

## Sections and links

Sections group related links under a title and optional description. Links can include:

- visible text;
- supporting description;
- navigation target;
- icon or image;
- alternative text;
- audience targeting.

Supported image formats include JPG, JPEG, PNG, GIF, WebP, and SVG. Confirm that ordinary users can read every selected image.

## Featured content and panel footer

Top-level panels can include:

- featured title and description;
- footer text;
- one or more footer buttons.

A footer button without a URL is disabled.

## Audience targeting

Audience targeting can be applied to supported actions, items, links, sections, and footer buttons.

1. Expand the entry in Settings.
2. Under **Audience targeting**, select one Microsoft Entra group.
3. Save and verify with a member and non-member account.

Rules:

- no selected group means the entry is available to everyone;
- a selected group limits the entry to members of that group;
- if membership resolution fails, targeted entries are hidden while untargeted entries remain visible;
- audience targeting controls presentation only and does not grant access to the destination.

## Home and breadcrumbs

- The item with key `home` navigates to the tenant root.
- The breadcrumb starts at the tenant root and ends at the current SharePoint location.
- SharePoint single-page navigation updates the menu and breadcrumb without a full reload.

Each save replaces the complete shared configuration. Coordinate changes when multiple managers are working at the same time.
