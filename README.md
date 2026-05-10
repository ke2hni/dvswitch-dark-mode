<p align="center">
  <img src="https://raw.githubusercontent.com/ke2hni/.github/main/assets/dvswitch-dark-banner.png" alt="DVSwitch Dashboard Dark Mode" width="100%">
</p>

<h1 align="center">DVSwitch Dashboard Dark Mode Overlay</h1>

<p align="center">
  Lightweight Auto / Light / Dark theme overlay for the stock DVSwitch Dashboard
  <br>
  Built for ASL3 / Debian 13 systems
</p>

---

# DVSwitch Dashboard Dark Mode Overlay

A lightweight modern dark-mode overlay system for the stock DVSwitch Dashboard.

This project adds:

- Auto / Light / Dark theme support
- Responsive dark styling
- AJAX-safe live table theming
- Preserved semantic network/status colors
- Safe rollback support
- Protected factory backups
- Reversible overlay patching

The goal is to modernize the dashboard appearance while:

- preserving original DVSwitch functionality
- preserving upstream runtime behavior
- avoiding large rewrites
- remaining lightweight
- remaining safe for production nodes

---

# Features

## Auto / Light / Dark Modes

Theme selector added directly into the dashboard header:

- Auto
  - follows browser/system dark mode
- Light
  - original-style light dashboard
- Dark
  - modern dark dashboard

---

## AJAX-Safe Live Activity Styling

The DVSwitch dashboard refreshes several sections every 1.5 seconds.

This overlay safely re-applies dark styling after live updates for:

- Gateway Activity
- Local Activity

without breaking live RX/TX updates or semantic colors.

---

## Semantic Status Color Preservation

The overlay intentionally preserves important live colors such as:

- RX/TX indicators
- BER/Loss indicators
- Green/Red/Orange status cells
- Temperature threshold colors

No destructive global recoloring is performed.

---

## Safe Backup / Restore System

The script automatically creates:

### Protected Original Backup

Created once:

/usr/share/dvswitch/.dvs-dashboard-original-backup

This backup is never overwritten.

---

### Per-Run Backups

Created on every apply:

/usr/share/dvswitch/.dvs-dashboard-theme-backup-YYYYMMDD-HHMMSS

Allows safe rollback/testing.

---

# Supported Systems

Tested on:

- ASL3
- Debian 13 (Trixie)
- Raspberry Pi 4
- Raspberry Pi 5

Designed for:

- DVSwitch Server dashboard
- production nodes
- test nodes
- lab systems

---

# Installation

## Quick Install

Download the script:

wget https://raw.githubusercontent.com/ke2hni/DVSwitch-Dark-Mode/main/dvswitch-dark-mode.sh

Make executable:

chmod +x dvswitch-dark-mode.sh

Run the installer:

sudo ./dvswitch-dark-mode.sh

---

# Menu Options

1 = Apply Auto/Light/Dark theme toggle
2 = Restore latest run backup
3 = Restore original factory dashboard files
0 = Exit

---

# What The Script Modifies

The overlay safely works with:

/usr/share/dvswitch/index.php
/usr/share/dvswitch/css/css.php
/usr/share/dvswitch/css/css-mini.php
/usr/share/dvswitch/include/status.php
/usr/share/dvswitch/include/lh.php
/usr/share/dvswitch/include/localtx.php
/usr/share/dvswitch/include/system.php

Additional overlay files created:

/usr/share/dvswitch/css/dvs-theme.css
/usr/share/dvswitch/scripts/dvs-theme.js

---

# Design Philosophy

This project intentionally avoids:

- large dashboard rewrites
- replacing runtime logic
- destructive theme engines
- unsafe global CSS replacements

Instead it uses:

- surgical CSS overlays
- lightweight JS helpers
- AJAX-safe post-refresh styling
- reversible patch logic

---

# Important Notes

## This Is An Overlay System

This project is NOT a replacement dashboard.

It overlays styling onto the stock DVSwitch dashboard while preserving:

- dashboard logic
- refresh behavior
- live updates
- upstream compatibility

---

## AJAX Refresh Awareness

Several dashboard sections refresh dynamically.

Examples:

$("#lastHerd").load("include/lh.php"...)
$("#localTxs").load("include/localtx.php"...)

Because of this:

- broad CSS replacements are unsafe
- global recoloring is avoided
- section-specific targeting is required

---

# Restore Options

## Restore Latest Backup

Restores the most recent backup created by the script.

---

## Restore Factory Dashboard

Restores the original untouched dashboard files from the protected original backup.

This allows returning to the stock dashboard without reinstalling DVSwitch.

---

# Project Goals

Long-term goals include:

- cleaner modern UI
- additional theme options
- accessibility improvements
- compact mode
- update-safe overlays
- GitHub release packaging
- public installer/uninstaller support

while still remaining:

- lightweight
- reversible
- upstream-friendly
- safe for real radio systems

---

# Screenshot Goals

Recommended future screenshots:

- Light Mode
- Dark Mode
- Auto Mode
- Gateway Activity
- Local Activity
- Hardware Info
- Mobile/Responsive Layout

---

# Author

KE2HNI

---

# License

MIT License

Use at your own risk.

Always test on a non-production node first.
