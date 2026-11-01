# Carter+ --- README

**Version:** 2.3.0\
**Author:** Jass\
**Script name:** Carter+\
**Platform:** Tampermonkey\
**Supported websites:** Ticketmaster domains listed below

------------------------------------------------------------------------

## Overview

Carter+ is a browser userscript created by **Jass**. It adds a compact
control panel to supported Ticketmaster pages. When enabled, you can
draw a selection box over an area of the seat map or ticket controls.
The script scans the selected area, attempts to identify available
selectable items, selects according to the configured quantity, and
attempts to activate the matching Reserve control.

Carter+ is an assistance tool. It does not guarantee that tickets will
be available, selected, or reserved. Website layouts and booking flows
can change at any time.

## Features

-   Compact on-page control panel with a dark, green interface.
-   Adjustable selection quantity from 1 to 10.
-   Single-selection and multi-selection modes.
-   Box selection using a keyboard modifier and mouse drag.
-   Automatic scanning of the selected region.
-   Attempts to select matching available items and activate a Reserve
    control.
-   Activity log displayed in the panel.
-   Reset control to clear the current selection boxes.
-   Panel can be moved by dragging its header.
-   Panel and settings state are retained for the current browser tab
    session.

## Supported websites

The current script header matches these Ticketmaster domains:

-   `ticketmaster.com`
-   `ticketmaster.ca`
-   `ticketmaster.co.uk`
-   `ticketmaster.com.au`
-   `ticketmaster.de`
-   `ticketmaster.fr`

The script does not currently declare support for every Ticketmaster
country domain. It is configured to run only on the domains listed
above.

## Requirements

-   A desktop browser that supports the Tampermonkey extension.
-   Tampermonkey installed and enabled.
-   The Carter+ userscript installed and enabled in Tampermonkey.
-   A supported Ticketmaster page.

The script is configured with `@run-at document-start` and does not
request Tampermonkey privileged APIs (`@grant none`).

------------------------------------------------------------------------

## Installation

### 1. Install Tampermonkey

1.  Open the browser's extension store.
2.  Search for **Tampermonkey** and install the official extension.
3.  Pin the Tampermonkey icon to the browser toolbar if you want quick
    access.

Useful links:

-   [Tampermonkey official website](https://www.tampermonkey.net/)
-   [Tampermonkey on the Chrome Web
    Store](https://chromewebstore.google.com/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo)

### 2. Add Carter+ to Tampermonkey

1.  Open the Tampermonkey extension menu.
2.  Open **Dashboard**.
3.  Select **Create a new script** (the plus/new-script option).
4.  A script editor will open.
5.  Remove the default template code.
6.  Open the Carter+ `.txt` or `.js` source file in a text editor.
7.  Copy the entire script, including the userscript header at the very
    top (`// ==UserScript==`).
8.  Paste the complete code into the Tampermonkey editor.
9.  Save the script with **Ctrl + S** (or **Cmd + S** on macOS).
10. Check that Carter+ appears in the Tampermonkey Dashboard and is
    enabled.

**Important:** Keep the userscript header intact. Tampermonkey uses its
metadata, including `@name` and `@match`, to identify the script and the
websites where it should run.

### 3. Open a supported Ticketmaster page

1.  Navigate to one of the supported Ticketmaster domains.
2.  Refresh the page after installing or changing the script.
3.  If the panel does not appear immediately, use the panel shortcut
    described below.

------------------------------------------------------------------------

## How to use Carter+

### 1. Open or hide the control panel

Press:

-   **Windows / Linux:** `Shift + Alt`
-   **macOS:** `Shift + Option`

Press the same key combination again to toggle the panel. The panel is
initially hidden.

The panel can be moved by dragging its header.

### 2. Turn the script on

In the panel, find **power** and click the switch to turn it on.

-   **ON:** Carter+ can respond to the selection-box gesture.
-   **OFF:** The selection workflow is disabled and existing selection
    boxes are cleared.

The script starts with power off by default.

### 3. Set the quantity

Click the number beside **quantity** to cycle through the available
values:

`1 → 2 → 3 → ... → 10 → 1`

Set the quantity to the number of seats or ticket items you want the
script to look for in the selected area.

### 4. Choose a selection mode

Click the **mode** control to switch between:

-   **single:** A new selection box replaces the previous selection box.
-   **multi:** You can create multiple separate selection boxes. The
    script ignores a new box if it overlaps an existing one or starts
    inside an existing box.

### 5. Draw a selection box

1.  Make sure power is ON.
2.  Set the quantity and mode.
3.  Move the pointer to the area you want Carter+ to scan.
4.  Hold **Ctrl** and drag the left mouse button to draw a rectangle
    around the desired seats or ticket controls.
5.  Release the mouse button to finish the box.
6.  Carter+ scans the selected region and attempts the
    selection/reservation workflow.

On macOS, the script uses **Command (⌘)** instead of Ctrl for the
selection-box gesture.

**Tip:** Draw a box around the intended selectable items, not the entire
page. Make sure the relevant seats or ticket controls are visible before
drawing.

### 6. Read the activity log

The panel displays status messages as the script works. Messages may
indicate that a selection box was created, a scan is running, items were
selected, a Reserve control was clicked, or the script is waiting for
the next page state.

The log is diagnostic feedback; it is not confirmation that a booking
has been completed.

### 7. Reset the selection

Click the **reset** button (the circular arrow in the panel header) to
clear the current selection boxes and reset the reservation flag used by
the script.

------------------------------------------------------------------------

## Important behavior and limitations

-   Carter+ is configured for the Ticketmaster domains listed in this
    README only.
-   The script attempts to identify selectable elements from the page.
    Ticketmaster may change its page structure, seat map, controls, or
    booking flow, which can affect detection.
-   The script can only act on items that the page exposes as selectable
    and that are detected as available.
-   A Reserve-button click is not proof of a successful reservation.
    Always check the website's own confirmation and checkout status.
-   The script suspends its selection workflow on URLs containing
    checkout or authorization, and hides its panel on those pages.
-   The script does not guarantee a particular seat, price, quantity, or
    successful checkout.
-   Do not use the script to bypass queues, access controls, purchase
    limits, CAPTCHA, anti-bot systems, or other website protections.
-   Use only where you are authorized to test or interact with the site,
    and follow Ticketmaster's terms and all applicable laws and event
    rules.

## Troubleshooting

### The panel does not appear

1.  Confirm Tampermonkey is installed and enabled.
2.  Confirm Carter+ is enabled in the Tampermonkey Dashboard.
3.  Confirm you are on one of the supported Ticketmaster domains.
4.  Refresh the page.
5.  Press `Shift + Alt` (or `Shift + Option` on macOS).

### Ctrl + drag does nothing

1.  Open the panel and turn **power** ON.
2.  Confirm the page has finished loading the seat map or ticket
    controls.
3.  Use the correct modifier: Ctrl on Windows/Linux, Command on macOS.
4.  Draw the box over visible seats or ticket controls.
5.  Check the activity log for scan or selection messages.

### The wrong number of items is selected, or nothing is selected

-   Check the quantity value before drawing the box.
-   Draw a tighter box around the intended items.
-   Make sure the items are visible and appear available on the website.
-   Try a fresh page load if the page has changed or become
    unresponsive.
-   Remember that detection depends on the website's current page
    structure.

### The Reserve control is not activated

-   Confirm the intended items were detected and selected.
-   Check whether the page has enabled its Reserve control.
-   The site may have changed its interface or booking flow. Do not
    assume that a click means the reservation succeeded.

### The script stops on checkout or authorization pages

This is intentional in the current version. Carter+ suspends its
selection workflow on URLs that contain `checkout` or `authorization`.

------------------------------------------------------------------------

## Privacy

The current source does not declare external network requests, remote
code dependencies, or Tampermonkey privileged API grants. It uses the
current tab's session storage to retain a small amount of interface
state and reservation-flow state. The script also interacts with the
Ticketmaster page on which it runs.

This description is based on the supplied Carter+ v2.3.0 source. Review
the source yourself before installing or using any userscript.

------------------------------------------------------------------------

## License --- Jass

**Copyright (c) 2026 Jass. All rights reserved.**

Carter+ is an original userscript authored and maintained by **Jass**.

Unless Jass gives prior written permission:

1.  You may install and use an unmodified copy for your own personal
    use.
2.  You may not sell, rent, sublicense, redistribute, or publicly
    re-upload the script or substantial portions of its source code.
3.  You may not remove or alter the author credit, copyright notice, or
    license notice.
4.  You may not publish modified or derivative versions as your own
    work.
5.  You may not use the script in a way that violates applicable law, a
    website's terms, purchase limits, or access restrictions.

**No warranty:** The script is provided "AS IS", without warranties or
guarantees of any kind. Jass is not responsible for failed selections,
missed tickets, unsuccessful reservations, account restrictions, losses,
or other damages arising from use of the script, to the maximum extent
permitted by applicable law.

This is a custom permission notice for Carter+; it is not a claim that
the script is licensed under MIT, GPL, Apache, or another standard
open-source license. For permissions beyond personal use, contact the
author and obtain written approval.

------------------------------------------------------------------------

## Credits

**Created by:** Jass\
**Project:** Carter+\
**Version documented:** 2.3.0

Please retain the author credit when keeping your personal copy.
