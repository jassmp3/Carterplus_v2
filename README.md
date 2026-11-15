Carter+ --- README

Version: 2.7.0
Author: Jass
Script name: Carter+
Platform: Tampermonkey
Supported websites: Ticketmaster domains listed below

Overview

Carter+ is a browser userscript created by Jass. It adds a compact control panel to supported Ticketmaster pages. When enabled, you Ctrl + drag over an area of the seat map (or ticket controls), and the script finds the available seats there, selects them, and attempts to activate the matching Reserve control.

Carter+ has three modes, each with its own box colour and its own type options:

Mode	Box colour	Best for	Type options
select+	Blue	Selecting every available seat in an area, instantly	selection (drag box, default) / pen (marker line)
smart	Red	Watching an area and grabbing a group of adjacent seats as soon as they appear	single / multi
add+	Gold	Events where each seat opens a ticket-type panel and must be added one by one (presales, offer codes, multi-price seats)	best / cheaper

Carter+ is an assistance tool. It does not guarantee that tickets will be available, selected, or reserved. Website layouts and booking flows can change at any time.

Features
Compact on-page control panel with a dark, green interface and a live activity log.
Three working modes: select+, smart and add+.
Adjustable quantity from 1 to 10.
Box selection with a keyboard modifier and mouse drag, or a pen/marker line in select+ mode.
Automatic scanning of the selected region (smart and add+).
Automatic click on the Reserve control after selecting.
Automatic handling of common confirmation dialogs, including the wheelchair/accessible "Agree & Continue" prompt.
Single-seat protection: when a group of seats would leave one seat open, the script takes the extra seat too instead of leaving it orphaned.
Add+ workflow that mimics the manual "select seat, choose ticket type, press Add" routine and then reserves.
Audible siren alert when a reservation carries you to the checkout page.
Reset control to clear the current boxes and strokes.
Panel can be moved by dragging its header.
Settings are retained for the current browser tab session.
Supported websites

The current script header matches these Ticketmaster domains:

ticketmaster.com
ticketmaster.ca
ticketmaster.co.uk
ticketmaster.com.au
ticketmaster.de
ticketmaster.fr

The script does not declare support for every Ticketmaster country domain. It is configured to run only on the domains listed above.

Requirements
A desktop browser that supports the Tampermonkey extension.
Tampermonkey installed and enabled.
The Carter+ userscript installed and enabled in Tampermonkey.
A supported Ticketmaster page.

The script is configured with @run-at document-start and does not request Tampermonkey privileged APIs (@grant none).

Installation
1. Install Tampermonkey
Open the browser's extension store.
Search for Tampermonkey and install the official extension.
Pin the Tampermonkey icon to the browser toolbar if you want quick access.

Useful links:

Tampermonkey official website
Tampermonkey on the Chrome Web Store
2. Add Carter+ to Tampermonkey
Open the Tampermonkey extension menu.
Open Dashboard.
Select Create a new script (the plus/new-script option).
A script editor will open.
Remove the default template code.
Open the Carter+ .txt or .js source file in a text editor.
Copy the entire script, including the userscript header at the very top (// ==UserScript==).
Paste the complete code into the Tampermonkey editor.
Save the script with Ctrl + S (or Cmd + S on macOS).
Check that Carter+ appears in the Tampermonkey Dashboard and is enabled.

Important: Keep the userscript header intact. Tampermonkey uses its metadata, including @name and @match, to identify the script and the websites where it should run.

Updating: To update from an older version, open the existing Carter+ script in the Dashboard, replace its whole contents with the new source, and save.

3. Open a supported Ticketmaster page
Navigate to one of the supported Ticketmaster domains.
Refresh the page after installing or changing the script.
If the panel does not appear immediately, use the panel shortcut described below.
The control panel

Press:

Windows / Linux: Shift + Alt
macOS: Shift + Option

Press the same combination again to hide the panel. The panel is initially hidden, and it can be moved by dragging its header.

The panel is laid out as a small settings block:

Setting	What it does
power	Switch that turns the script on or off. Defaults to on. Turning it off clears all boxes and strokes.
mode	Click to cycle select+ → smart → add+ → select+.
quantity	Click to cycle 1 → 2 → ... → 10 → 1. Used by smart and add+ (see the mode sections). Defaults to 2.
type	Click to toggle the options for the current mode (see the table above).
↻ (header button)	Clears all boxes, strokes and the reservation flag.

Defaults on a fresh tab: power on, mode select+, type selection, quantity 2, add+ type best. Your choices are kept for the current browser tab session only.

Switching mode or type clears the boxes and strokes currently on screen.

The selection gesture

In every mode, selection starts with:

Windows / Linux: hold Ctrl and drag with the left mouse button.
macOS: hold Command (⌘) and drag with the left mouse button.

Press Esc during a drag to cancel it. Make sure the relevant seats are visible on screen before you draw.

Mode 1: select+ (blue)

Select+ selects every available seat under your mark in one go, then clicks Reserve. The quantity setting is not used in this mode.

Type: selection (default)
Hold Ctrl and drag a rectangle over the seats you want. The box is blue.
When you release Ctrl (or the mouse, if Ctrl is already up), all available seats under the box are selected at once.
The script verifies the clicks registered, retries any that did not, and clicks Reserve.

Drawing a new box replaces the previous one.

Type: pen
Hold Ctrl and draw a short marker line over the seats you want. The line glows blue.
Any available seat the line passes over (or very close to) is picked. A single Ctrl + click picks one seat.
You can draw several strokes while Ctrl stays held. Everything under all strokes is selected when you release Ctrl.
The script then selects the seats and clicks Reserve, exactly as in selection type.

The pen has no effect on seats the line merely passes near the next row over; draw along the row you want.

Details common to both types
Seats already picked in this session are skipped if you draw over them again, so you can add seats in batches. Use reset to clear that memory.
If a single seat would be left open next to your selection and the site warns about it, the script adds the nearest extra seat and reserves again.
Mode 2: smart (red)

Smart mode watches the area you boxed and acts the moment enough seats are available.

Set quantity to the number of seats you need.
Hold Ctrl and drag a red box over the area.
The box stays armed and pulses. The script keeps scanning inside it.
As soon as a group of adjacent seats of your quantity appears, it selects them and clicks Reserve.
If the site rejects the seats, a dialog appears, or the seats are released, the script re-arms the box and tries again.
Type: single / multi
single: a new box replaces the previous one.
multi: you can keep several separate boxes at once. A new box is ignored if it overlaps an existing box or starts inside one.
Single-seat protection

If the best group of adjacent seats would leave exactly one seat open next to your quantity (for example you want 2 and a run of 3 appears), the script takes all 3 rather than leaving the single seat stranded.

Mode 3: add+ (gold)

Add+ is for events where the seat map cannot be bulk-selected because each seat opens a ticket-type panel (for example presales, venue codes, offers, or seats with several price options). Normally you would:

Select one seat.
The side panel opens with the ticket types. Press Add.
Back on the map, select the next seat and press Add again.
When you have all your seats, press Reserve Tickets.

Add+ does exactly that, automatically.

How to use it
Switch mode to add+.
Set quantity and choose the type (best or cheaper).
Hold Ctrl and drag a gold box over the area. The box stays armed until the work is done.
When seats appear under the box, add+ takes over:
finds a group of adjacent seats of your quantity (with the same single-seat protection as smart mode),
clicks the first seat and waits for the ticket-type panel,
applies the chosen type (below) and presses Add,
waits for the map to come back, then repeats for the next seat,
finally presses Reserve Tickets.
Type: best

Presses Add on every seat, whatever price option is currently selected in the panel. This suits events where the panel already defaults to the option you want (for example the code price).

Type: cheaper

Reads the prices of the ticket-type options in the panel, selects the cheapest one (if it is not already selected), and then presses Add. It does this for every seat.

Recovery behaviour
If a seat click does not open the panel, the script retries the click a couple of times.
If a seat cannot be added, the script re-scans and only looks for the remaining number of seats, keeping the ones already added.
If the site shows the single-seat warning after Reserve, the script adds the nearest extra seat through the same select-and-Add routine and reserves again.
If some seats are dropped after Reserve, it keeps the ones still held and adds only the missing ones.
After repeated failed attempts it stops and logs that it gave up.

In add+ mode the ticket-selection side panel is protected from the script's dialog-closing helper, so the panel is not closed before Add is pressed.

Dialogs, alerts and checkout
Dialogs: while a box or stroke is active, the script clears common blocking dialogs by pressing buttons such as Agree & Continue, Continue, OK, Confirm or Close. This is what handles the wheelchair/accessible-seat prompt.
Siren: if a Reserve click takes you to a checkout page within about ten minutes, the script plays a short siren so you notice.
Checkout pages: the script suspends itself on URLs containing checkout or authorization and hides its panel there.
Reading the activity log

Lines are JSON-style status messages. Bright lines mark key events (found, selected, add, price, reserve, dialog, orphan, alarm); dim lines are routine scans and waiting messages.

Typical add+ sequence:

found --- a group of seats was detected in the box.
add: seat --- clicking seat n of total.
add: panel --- ticket-type panel opened (with the option count and cheapest price in cheaper type).
price: picked / already cheapest --- the price option chosen.
add: clicked / add: added --- Add pressed and confirmed.
reserve: clicked --- Reserve Tickets pressed.

The log is diagnostic feedback; it is not confirmation that a booking has been completed.

Important behavior and limitations
Carter+ is configured for the Ticketmaster domains listed in this README only.
The script identifies seats, buttons and price options from the page structure. Ticketmaster may change its seat map, panels or booking flow, which can affect detection.
The script can only act on items the page exposes as selectable and that appear available.
Add+ relies on finding a button labelled Add and a Reserve button, and (for cheaper) on price options with visible prices. Unusual layouts may not be recognised.
A Reserve click is not proof of a successful reservation. Always check the website's own confirmation and checkout status.
The script does not guarantee a particular seat, price, quantity, or successful checkout.
Do not use the script to bypass queues, access controls, purchase limits, CAPTCHA, anti-bot systems, or other website protections.
Use only where you are authorized to test or interact with the site, and follow Ticketmaster's terms and all applicable laws and event rules.
Troubleshooting
The panel does not appear
Confirm Tampermonkey is installed and enabled.
Confirm Carter+ is enabled in the Tampermonkey Dashboard.
Confirm you are on one of the supported Ticketmaster domains.
Refresh the page.
Press Shift + Alt (or Shift + Option on macOS).
Ctrl + drag does nothing
Open the panel and make sure power is on.
Confirm the seat map has finished loading.
Use the correct modifier: Ctrl on Windows/Linux, Command on macOS.
Draw over visible seats.
Check the activity log for messages.
Select+ says "no seats under the box / marker"
The mark did not cover any available seats. Redraw it over the seats, or draw closer to the centre of each seat in pen type.
Seats already picked earlier in the session are skipped. Press reset and try again.
Smart mode finds nothing
Check the quantity and draw the box over a row or block where a run of adjacent seats can appear.
On events where every seat opens a ticket-type panel, use add+ instead.
Add+ gets stuck or fails
Check the log: no add button means the panel did not open after clicking the seat; not confirmed means Add did not seem to take.
For cheaper, a pick failed line means the cheapest option could not be selected; the script still presses Add, so check the price.
Make sure the box covers seats that are clickable and visible.
The wrong number of seats is selected
Check the quantity (smart and add+) before drawing the box.
Draw a tighter box around the intended seats.
Remember that single-seat protection may take one extra seat to avoid leaving a lone seat.
The script stops on checkout or authorization pages

This is intentional. Carter+ suspends itself on URLs that contain checkout or authorization.

Privacy

The current source does not declare external network requests, remote code dependencies, or Tampermonkey privileged API grants. It uses the current tab's session storage to retain a small amount of interface state (power, mode, quantity, types) and reservation-flow state. The script also interacts with the Ticketmaster page on which it runs.

This description is based on the supplied Carter+ v2.7.0 source. Review the source yourself before installing or using any userscript.

Version history
2.7.0 --- Added add+ mode (gold box) with best and cheaper types: select a seat, choose ticket type, press Add, repeat, then reserve.
2.6.0 --- Select+ gets a type option: selection (default drag box) or pen.
2.5.0 --- Added the pen/marker style for select+.
2.3.0 --- Previously documented release.
License --- Jass

Copyright (c) 2026 Jass. All rights reserved.

Carter+ is an original userscript authored and maintained by Jass.

Unless Jass gives prior written permission:

You may install and use an unmodified copy for your own personal use.
You may not sell, rent, sublicense, redistribute, or publicly re-upload the script or substantial portions of its source code.
You may not remove or alter the author credit, copyright notice, or license notice.
You may not publish modified or derivative versions as your own work.
You may not use the script in a way that violates applicable law, a website's terms, purchase limits, or access restrictions.

No warranty: The script is provided "AS IS", without warranties or guarantees of any kind. Jass is not responsible for failed selections, missed tickets, unsuccessful reservations, account restrictions, losses, or other damages arising from use of the script, to the maximum extent permitted by applicable law.

This is a custom permission notice for Carter+; it is not a claim that the script is licensed under MIT, GPL, Apache, or another standard open-source license. For permissions beyond personal use, contact the author and obtain written approval.

Credits

Created by: Jass
Project: Carter+
Version documented: 2.7.0

Please retain the author credit when keeping your personal copy.
