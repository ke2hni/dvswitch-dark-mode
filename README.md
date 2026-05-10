# 🌙 DVSwitch Dashboard Dark Mode Overlay

<p align="center">
  <img src="https://img.shields.io/badge/DVSwitch-Dark%20Mode%20Overlay-blueviolet?style=for-the-badge">
  <img src="https://img.shields.io/badge/Version-v0.25--test-brightgreen?style=for-the-badge">
  <img src="https://img.shields.io/badge/Debian%2013-Trixie-red?style=for-the-badge&logo=debian">
  <img src="https://img.shields.io/badge/ASL3-Compatible-success?style=for-the-badge">
</p>

---

## 📌 Overview

The **DVSwitch Dashboard Dark Mode Overlay** adds a modern Auto / Light / Dark theme system to the stock DVSwitch Dashboard while preserving original dashboard functionality and upstream behavior.

This project is designed around:

```text
Safe overlay patching
Minimal file modification
AJAX-safe dark styling
Production-safe rollback support
```

The goal is to modernize the dashboard appearance without replacing the original DVSwitch dashboard logic.

---

## 📥 Installation

```bash
git clone https://github.com/ke2hni/DVSwitch-Dark-Mode.git
cd DVSwitch-Dark-Mode
chmod +x dvswitch-dark-mode.sh
sudo ./dvswitch-dark-mode.sh
```

---

## 🎨 Features

### 🌗 Auto / Light / Dark Theme Modes

Adds a live theme selector directly into the dashboard header:

| Mode  | Description                      |
| ----- | -------------------------------- |
| Auto  | Follows browser/system dark mode |
| Light | Original-style light dashboard   |
| Dark  | Modern dark dashboard            |

---

### ⚡ AJAX-Safe Live Dashboard Styling

The DVSwitch dashboard refreshes several sections every 1.5 seconds.

This overlay safely preserves dark mode styling during live updates for:

* Gateway Activity
* Local Activity

without breaking live RX/TX activity or dashboard refresh logic.

---

### 🎯 Semantic Color Preservation

The overlay intentionally preserves important live dashboard colors including:

* RX/TX indicators
* BER/Loss indicators
* Status colors
* CPU temperature threshold colors
* Network activity indicators

No destructive global recoloring is performed.

---

### 🛡️ Safe Backup / Restore System

The script automatically creates:

#### Protected Original Backup

```text
/usr/share/dvswitch/.dvs-dashboard-original-backup
```

Created once and never overwritten.

---

#### Per-Run Backups

```text
/usr/share/dvswitch/.dvs-dashboard-theme-backup-YYYYMMDD-HHMMSS
```

Created during every apply operation for safe rollback/testing.

---

## 📋 Menu

```text
DVSwitch Dashboard Theme Overlay v0.25-test

1 = Apply Auto/Light/Dark theme toggle
2 = Restore latest run backup
3 = Restore original factory dashboard files
0 = Exit
```

---

## 🧩 What The Script Modifies

### Dashboard Files

```text
/usr/share/dvswitch/index.php
/usr/share/dvswitch/css/css.php
/usr/share/dvswitch/css/css-mini.php
/usr/share/dvswitch/include/status.php
/usr/share/dvswitch/include/lh.php
/usr/share/dvswitch/include/localtx.php
/usr/share/dvswitch/include/system.php
```

### Overlay Files Created

```text
/usr/share/dvswitch/css/dvs-theme.css
/usr/share/dvswitch/scripts/dvs-theme.js
```

---

## 🧠 Design Philosophy

This project intentionally avoids:

* large dashboard rewrites
* replacing runtime dashboard logic
* unsafe global CSS replacements
* destructive theme engines

Instead it uses:

* surgical CSS overlays
* lightweight JavaScript helpers
* AJAX-safe post-refresh styling
* reversible patch logic

---

## 🔄 AJAX Refresh Awareness

Several DVSwitch dashboard sections refresh dynamically.

Examples:

```javascript
$("#lastHerd").load("include/lh.php"...)
$("#localTxs").load("include/localtx.php"...)
```

Because of this:

* broad CSS replacements are unsafe
* global recoloring is avoided
* section-specific targeting is required

This overlay safely re-applies styling after refresh events.

---

## 🔁 Restore Options

### Restore Latest Backup

Restores the most recent backup created by the script.

---

### Restore Factory Dashboard

Restores the original untouched dashboard files from the protected original backup.

Allows returning to stock DVSwitch dashboard files without reinstalling DVSwitch.

---

## 🧪 Tested Systems

* Debian 13 / Trixie
* ASL3
* Raspberry Pi 4
* Raspberry Pi 5

Tested against:

* production nodes
* lab nodes
* responsive-layout patched systems

---

## 🎯 Long-Term Project Goals

Future goals include:

* cleaner modern UI
* additional themes
* compact mode
* accessibility improvements
* user-selectable accent colors
* update-safe overlays
* GitHub release packaging
* install/uninstall helper scripts

while remaining:

```text
lightweight
reversible
upstream-friendly
safe for real radio systems
```

---

## 📌 Current Stable Baseline

```text
dvswitch-dark-mode.sh
Theme Overlay Baseline: v0.25-test
```

Includes:

* Auto / Light / Dark modes
* AJAX-safe Gateway Activity theming
* AJAX-safe Local Activity theming
* Hardware Info dark styling
* protected factory backups
* restore support
* backup-folder creation fix

---

## 📜 License

Use at your own risk.

Always test on a non-production node first.

---

<p align="center">
  🌙 Built to modernize DVSwitch Dashboard safely without breaking upstream behavior
</p>
<img width="1600" height="900" alt="Screenshot 2026-05-10 001836" src="https://github.com/user-attachments/assets/9e5d2256-4e42-474c-bdf3-2c011afb1937" />
