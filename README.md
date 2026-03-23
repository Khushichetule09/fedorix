<div align="center">

# Fedorix 🐧

**A clean, minimal GNOME customization for Fedora, built for people who want their desktop to look good without breaking their workflow.**

![GNOME](https://img.shields.io/badge/DE-GNOME-informational?style=flat&logo=gnome&logoColor=white&color=4A90D9)
![Distro](https://img.shields.io/badge/Distro-Fedora-informational?style=flat&logo=fedora&logoColor=white&color=3c6eb4)
![License](https://img.shields.io/badge/License-MIT-green.svg)

![Overview](Assets/overview.png)

</div>

---

### Table of Contents

- [Introduction](#introduction)
- [Preview](#preview)
- [Appearance](#appearance)
  - [System & Icon Theme (Yaru)](#system--icon-theme-yaru)
  - [Cursor Theme (macOS Cursor)](#cursor-theme-macos-cursor)
  - [Sound Theme (MIUI)](#sound-theme-miui)
  - [Fonts (Ubuntu)](#fonts-ubuntu)
- [Extensions](#extensions)
  - [Visual Extensions](#visual-extensions)
  - [Usability Extensions](#usability-extensions)
  - [Extension Configurations](#extension-configurations)
- [Setup Guide](#setup-guide)
- [Applications](#applications)
  - [Firefox (Add Water)](#firefox-add-water)
  - [Zen Browser](#zen-browser)
  - [Clipboard Manager](#clipboard-manager)
  - [Terminal](#terminal)
  - [VS Code & Dev Environment](#vs-code--dev-environment)
- [Extras](#extras)
  - [Distrobox](#distrobox)
  - [Winboat](#winboat)
  - [Emoji Picker](#emoji-picker)
  - [Alt + Drag Windows](#alt--drag-windows)
- [Directory Structure](#directory-structure)
- [Credits](#credits)

---

## Introduction

I wanted something I could actually use every day. The goal was to keep it clean and minimal while avoiding unnecessary tweaks and visual clutter. 

GNOME felt like the right base after some tweaking. The overview workflow is smooth, and with a few extensions, it covers everything needed without getting in the way. It is not perfect, but it is at a point where it feels consistent and comfortable to use.

> [!IMPORTANT]
> Most of the visual polish comes from **configuring** extensions rather than just installing them. Make sure to check the [Extension Configurations](#extension-configurations) screenshots because the defaults will not get you there.

---
## Preview

![Multitasking](Assets/multitasking.png)

![Overview Search](Assets/overview-search.png)

![App Menu](Assets/app-menu.png)

![Launchpad](Assets/launchpad.png)

![System Apps](Assets/system-apps.png)

---

## Appearance

To apply these themes, make sure you have **GNOME Tweaks** installed. 

### System & Icon Theme (Yaru)

The Yaru dark theme from Ubuntu is clean and consistent. To keep things simple and avoid build systems, we will install it manually.

🔗 [github.com/ubuntu/yaru](https://github.com/ubuntu/yaru)

**Installation:**

```bash
git clone https://github.com/ubuntu/yaru.git
mkdir -p ~/.themes ~/.icons
cd yaru
cp -r themes/Yaru* ~/.themes/
cp -r icons/Yaru* ~/.icons/
```

**Applying the theme:**

Open **GNOME Tweaks → Appearance** and set:
- **Icons**: `Yaru-Dark`
- **Shell**: `Yaru-Dark` *(requires the **User Themes** extension)*
- **Legacy Applications**: `Yaru-Dark`

![Shell Appearance Config](configs/gnome-tweaks/shell-appearence-config.png)

---

### Cursor Theme (macOS Cursor)

🔗 [gnome-look.org/p/1408466](https://www.gnome-look.org/p/1408466)

**Installation:**

Download and extract the theme from the link above, then copy it to your icons folder:

```bash
mkdir -p ~/.icons
cp -r <extracted-folder> ~/.icons/
```

**Applying the theme:**

Open **GNOME Tweaks → Appearance** and select the macOS cursor.

---

### Sound Theme (MIUI)

🔗 [gnome-look.org/p/1375637](https://www.gnome-look.org/p/1375637)

**Installation:**

Download and extract the theme, then copy it to your sounds folder:

```bash
mkdir -p ~/.local/share/sounds
cp -r <extracted-folder> ~/.local/share/sounds/
```

**Applying the theme:**

Open **GNOME Tweaks → Sound** and select the theme.
*(Note: GNOME sound theme support can be inconsistent depending on the distro, so some sounds might not apply.)*

![Sound Theme Config](configs/gnome-tweaks/sound-theme.png)

---

### Fonts (Ubuntu)

🔗 [fonts.google.com/specimen/Ubuntu](https://fonts.google.com/specimen/Ubuntu)

**Installation:**

1. Download the font from Google Fonts using the link above.
2. Extract the `.zip` file.
3. Double click any `.ttf` file to open it in GNOME Font Viewer.
4. Click the **"Install"** button.

*(Optional Advanced Method)*:
```bash
mkdir -p ~/.local/share/fonts
cp *.ttf ~/.local/share/fonts/
fc-cache -fv
```

**Applying the fonts:**

Open **GNOME Tweaks → Fonts** and configure them as follows:

| Usage          | Font            |
|----------------|-----------------|
| Interface Text | `Ubuntu`        |
| Document Text  | `Ubuntu Medium` |
| Monospace Text | `Monospace`     |

![Font Config](configs/gnome-tweaks/font-config.png)

![Window Config](configs/gnome-tweaks/windows-config.png)

---

## Extensions

Extensions do a lot of the heavy lifting here. I have split them into visual and usability categories based on how I use them.

Install from [extensions.gnome.org](https://extensions.gnome.org) or use [Extension Manager](https://flathub.org/apps/com.mattjakeman.ExtensionManager) from Flathub.

![Extensions list 1](configs/gnome-extensions/1-extensions.png)

![Extensions list 2](configs/gnome-extensions/2-extensions.png)

---

### Visual Extensions

These extensions control how the desktop looks. Blur My Shell alone is responsible for most of the visual feel.

- [**Blur My Shell**](https://extensions.gnome.org/extension/3193/blur-my-shell/) - Adds blur to panels, the overview, and the dash. This is the single biggest visual upgrade.
- [**Just Perfection**](https://extensions.gnome.org/extension/3843/just-perfection/) - Hides and fine-tunes GNOME Shell UI elements.
- [**User Themes**](https://extensions.gnome.org/extension/19/user-themes/) - Required to apply a custom Shell theme.
- [**Compiz Magic Lamp Effect**](https://extensions.gnome.org/extension/3740/compiz-alike-magic-lamp-effect/) - Provides a smooth and satisfying minimize animation.
- [**Hide Top Bar**](https://extensions.gnome.org/extension/545/hide-top-bar/) - Auto hides the top panel when not needed.
- [**Top Bar Organiser**](https://extensions.gnome.org/extension/4356/top-bar-organizer/) - Controls what appears in the top bar and in what order.

---

### Usability Extensions

These extensions make day to day use smoother by providing launchers, tiling, a clipboard, and phone sync capabilities.

- [**ArcMenu**](https://extensions.gnome.org/extension/3628/arcmenu/) - Replaces the default app grid with a proper application launcher.
- [**Dash to Dock**](https://extensions.gnome.org/extension/307/dash-to-dock/) - Turns the GNOME dash into a persistent and customizable dock.
- [**Forge Tiling**](https://extensions.gnome.org/extension/4481/forge/) - Enables manual tiling window management.
- [**Tiling Shell**](https://extensions.gnome.org/extension/7065/tiling-shell/) - Provides auto tiling with screen edge snapping.
- [**GSConnect**](https://extensions.gnome.org/extension/1319/gsconnect/) - Integrates KDE Connect for phone and desktop synchronization.
- [**Copyous**](https://extensions.gnome.org/extension/8834/copyous/) - Adds a gnome native clipboard manager with a history view.
- [**Win11 Clipboard History**](https://github.com/gustavosett/Windows-11-Clipboard-History-For-Linux) - Adds a Windows 11 style `Win + V` clipboard panel.
- [**Quick Settings Audio Panel**](https://extensions.gnome.org/extension/5940/quick-settings-audio-panel/) - Improves audio controls inside the quick settings menu.
- [**GTK4 Desktop Icons NG (DING)**](https://extensions.gnome.org/extension/5263/gtk4-desktop-icons-ng-ding/) - Adds desktop icon support to GNOME.
- [**AppIndicator & KStatusNotifierItem Support**](https://extensions.gnome.org/extension/615/appindicator-support/) - Adds system tray icon support.
- [**Extension List**](https://extensions.gnome.org/extension/3088/extension-list/) - Allows you to manage and toggle extensions directly from the panel.
- [**Caffeine**](https://extensions.gnome.org/extension/517/caffeine/) - Prevents the screen from sleeping when you need it to stay on.

---

### Extension Configurations

> If I left some settings out, it is because I did not change them from the defaults.

<details>
<summary><b>Blur My Shell</b></summary>

**Pipelines**

![Pipelines](configs/gnome-extensions/0-extension-configrations/blur%20my%20shell/1-pipelines.png)

**Panel**

![Panel](configs/gnome-extensions/0-extension-configrations/blur%20my%20shell/2-panel.png)

**Overview**

![Overview](configs/gnome-extensions/0-extension-configrations/blur%20my%20shell/3-overview.png)

**Dash**

![Dash](configs/gnome-extensions/0-extension-configrations/blur%20my%20shell/4-dash.png)

**Applications**

![Applications](configs/gnome-extensions/0-extension-configrations/blur%20my%20shell/5-applications.png)

**Extras**

![Extras](configs/gnome-extensions/0-extension-configrations/blur%20my%20shell/6-others(extras).png)

</details>

<details>
<summary><b>ArcMenu</b></summary>

**General**

![General](configs/gnome-extensions/0-extension-configrations/ArcMenu/1-general.png)

**Standalone Runner & Hotkeys**

![Hotkeys](configs/gnome-extensions/0-extension-configrations/ArcMenu/2-standalone-runner-menu-hotkeys.png)

**Menu Layout**

![Layout](configs/gnome-extensions/0-extension-configrations/ArcMenu/3-menu-layout.png)

**Menu Theme**

![Theme](configs/gnome-extensions/0-extension-configrations/ArcMenu/4-menu-theme.png)

**Visual Appearance**

![Visual](configs/gnome-extensions/0-extension-configrations/ArcMenu/5-menu-visual-apparence.png)

**Fine Tune**

![Fine Tune](configs/gnome-extensions/0-extension-configrations/ArcMenu/6-fine-tune.png)

**Search Options**

![Search](configs/gnome-extensions/0-extension-configrations/ArcMenu/7-search-options.png)

**Menu Buttons**

![Buttons](configs/gnome-extensions/0-extension-configrations/ArcMenu/8-menu-buttons.png)

</details>

<details>
<summary><b>Dash to Dock</b></summary>

**Position & Size**

![Position](configs/gnome-extensions/0-extension-configrations/dash%20to%20dock/1-position&size.png)

**Launcher**

![Launcher](configs/gnome-extensions/0-extension-configrations/dash%20to%20dock/2-launcher.png)

**Behaviour**

![Behaviour](configs/gnome-extensions/0-extension-configrations/dash%20to%20dock/3-behaviour.png)

**Appearance**

![Appearance](configs/gnome-extensions/0-extension-configrations/dash%20to%20dock/4-appearence.png)

</details>

<details>
<summary><b>Just Perfection</b></summary>

**Behaviour**

![Behaviour](configs/gnome-extensions/0-extension-configrations/just%20perfection/1-behaviour.png)

**Customisation**

![Customisation 1](configs/gnome-extensions/0-extension-configrations/just%20perfection/2-customisation.png)

![Customisation 2](configs/gnome-extensions/0-extension-configrations/just%20perfection/3-customisation.png)

</details>

<details>
<summary><b>Forge Tiling</b></summary>

**Tiling**

![Tiling](configs/gnome-extensions/0-extension-configrations/forge-tiling/1-tiling.png)

**Appearance**

![Appearance](configs/gnome-extensions/0-extension-configrations/forge-tiling/2-appearence.png)

</details>

<details>
<summary><b>Tiling Shell</b></summary>

**Appearance**

![Appearance](configs/gnome-extensions/0-extension-configrations/tiling%20shell/1-apperarence.png)

**Behaviour**

![Behaviour](configs/gnome-extensions/0-extension-configrations/tiling%20shell/2-behaviour.png)

**Screen Edges**

![Screen Edges](configs/gnome-extensions/0-extension-configrations/tiling%20shell/3-screen-edeges.png)

</details>

<details>
<summary><b>GSConnect (KDE Connect)</b></summary>

**Sharing**

![Sharing](configs/gnome-extensions/0-extension-configrations/gsconnect(kde-connect)/1-sharing.png)

**Battery**

![Battery](configs/gnome-extensions/0-extension-configrations/gsconnect(kde-connect)/2-battery.png)

**Advanced / Experimental**

![Advanced](configs/gnome-extensions/0-extension-configrations/gsconnect(kde-connect)/3-advanced-experimental.png)

</details>

<details>
<summary><b>Quick Settings Audio Panel</b></summary>

**Extension Settings**

![Settings](configs/gnome-extensions/0-extension-configrations/quick%20settings%20audio%20panel/1-extension-settings.png)

**Element Order**

![Element Order](configs/gnome-extensions/0-extension-configrations/quick%20settings%20audio%20panel/2-elements-order.png)

</details>

<details>
<summary><b>Win11 Clipboard History</b></summary>

**Keyboard Shortcuts**

![Keyboard Shortcuts](configs/gnome-extensions/0-extension-configrations/win11-clipboard-history/1-keyboard-shortcuts.png)

**Personalisation**

![Personalisation](configs/gnome-extensions/0-extension-configrations/win11-clipboard-history/personalisation.png)

</details>

<details>
<summary><b>Copyous</b></summary>

**General**

![General](configs/gnome-extensions/0-extension-configrations/copyous/1-general.png)

**Customisation**

![Customisation](configs/gnome-extensions/0-extension-configrations/copyous/2-customisations.png)

</details>

<details>
<summary><b>GTK4 Desktop Icons NG (DING)</b></summary>

**Desktop**

![Desktop](configs/gnome-extensions/0-extension-configrations/gtk4%20desktop%20icons%20ng%20(ding)/1-desktop.png)

**Tweaks**

![Tweaks](configs/gnome-extensions/0-extension-configrations/gtk4%20desktop%20icons%20ng%20(ding)/2-tweaks.png)

**Files**

![Files](configs/gnome-extensions/0-extension-configrations/gtk4%20desktop%20icons%20ng%20(ding)/3-files.png)

</details>

<details>
<summary><b>User Themes</b></summary>

![Theme Modes](configs/gnome-extensions/0-extension-configrations/user%20themes/1-theme-modes.png)

</details>

<details>
<summary><b>Hide Top Bar</b></summary>

![Sensitivity](configs/gnome-extensions/0-extension-configrations/hide%20top%20bar/1-sensitivity.png)

</details>

<details>
<summary><b>Top Bar Organiser</b></summary>

![Top Bar Organiser](configs/gnome-extensions/0-extension-configrations/top%20bar%20oragniser/1-top%20bar%20organiser.png)

</details>

<details>
<summary><b>AppIndicator & KStatusNotifierItem Support</b></summary>

![General](configs/gnome-extensions/0-extension-configrations/Appindicator%20and%20KStatusNotifierItem%20Support/general-1.png)

</details>

<details>
<summary><b>Caffeine</b></summary>

![General](configs/gnome-extensions/0-extension-configrations/Caffiene/1-general.png)

</details>

<details>
<summary><b>Compiz Magic Lamp Effect</b></summary>

![Configuration](configs/gnome-extensions/0-extension-configrations/compiz%20alike%20magic%20lamp%20effect/1-configrations.png)

</details>

<details>
<summary><b>Extension List</b></summary>

![Configuration](configs/gnome-extensions/0-extension-configrations/extension%20list/1-configrations.png)

</details>

---

## Setup Guide

Here is a step by step guide to replicate this setup from a fresh Fedora install.

**1. Install GNOME Tweaks and Extension Manager**

```bash
sudo dnf install gnome-tweaks
flatpak install flathub com.mattjakeman.ExtensionManager
```

**2. Refer Appearance**

Refer to the [Appearance](#appearance) section for installing themes and fonts.

**3. Install Extensions**

Open Extension Manager or visit [extensions.gnome.org](https://extensions.gnome.org). Install everything listed in the [Extensions](#extensions) section, and configure each one using the screenshots in [Extension Configurations](#extension-configurations).

**4. Configure Apps**

Follow the per app instructions in the [Applications](#applications) section below.

> [!NOTE]
> The `configs/` folder is your reference for every setting. If something looks off, the answer is almost always in the extension config screenshots.

---

## Applications

### Firefox (Add Water)

Add Water makes Firefox look native on GNOME. It adds a cleaner titlebar, proper integration, and removes visual inconsistencies.

🔗 [flathub.org/apps/dev.qwery.AddWater](https://flathub.org/apps/dev.qwery.AddWater)

Install from Flathub, then configure as shown:

![Firefox](Assets/firefox.png)

---

### Zen Browser

A cleaner, more focused browser. The transparent tabs with blur look really good with this setup.

🔗 [zen-browser.app](https://zen-browser.app)

To enable transparent tabs:

1. Open `about:config`
2. Search for `browser.tabs.allow_transparent_browser`
3. Set it to `true`

![Zen Browser](Assets/zen.png)

> Blur My Shell handles the blur behind the browser. Make sure the Applications pipeline is enabled in its settings.

---

### Clipboard Manager

Two clipboard options are available here. Pick whichever fits your workflow better.

**Win11 Clipboard History** mimics the Windows 11 `Win + V` panel experience.

🔗 [github.com/gustavosett/Windows-11-Clipboard-History-For-Linux](https://github.com/gustavosett/Windows-11-Clipboard-History-For-Linux)

**Copyous** is a gnome native clipboard manager with a clean history view.

🔗 [extensions.gnome.org/extension/8834/copyous](https://extensions.gnome.org/extension/8834/copyous/)

**Clipboard panel:**

![Clipboard](Assets/1-clipboard.png)

**Animated preview:**

![Clipboard GIFs](Assets/clipboard-gifs.png)

---

### Terminal

No fancy terminal emulator is needed. You can just use the built in gnome terminal with the **Linux** profile for a minimal and clean look.

1. Open Terminal
2. Go to **Preferences** (`Ctrl + ,`)
3. Select the `Linux` theme

![Terminal](Assets/terminal.png)

---

### VS Code & Dev Environment

Install from the official website or your package manager.

**VS Code:**

![VS Code](Assets/vscode.png)

**Developer environment overview:**

![Developer Environment](Assets/devloper-inviroment.png)

---

## Extras

These are small additions that are not strictly part of the customization process, but they make the overall experience noticeably better.

---

### Distrobox

If you ever need an Arch or Ubuntu environment for testing, `.deb` packages, or tooling that isn't on Fedora, Distrobox is the cleanest solution. It runs containers on the shared kernel, providing no performance overhead without dual-booting.

🔗 [github.com/89luca89/distrobox](https://github.com/89luca89/distrobox)

```bash
curl -s https://raw.githubusercontent.com/89luca89/distrobox/main/install | sh
```

Once set up, spin up an Ubuntu container and install `.deb` packages directly on Fedora.

---

### Winboat

For the occasional Windows application that has no Linux alternative, Winboat handles it without a full dual-boot setup.

🔗 [github.com/TibixDev/winboat](https://github.com/TibixDev/winboat)

Follow the setup instructions in the repository.

---

### Emoji Picker

A quick emoji picker accessible from the panel is surprisingly useful once you have it.

![Emojis](Assets/2-emojis.png)

---

### Alt + Drag Windows

This lets you grab any part of a window to drag it without needing to aim for the titlebar. It is one of the best GNOME quality of life tweaks.

```bash
gsettings set org.gnome.desktop.wm.preferences mouse-button-modifier '<Alt>'
gsettings set org.gnome.desktop.wm.preferences resize-with-right-button true
```

To switch windows across all workspaces instead of just the current one:

```bash
gsettings set org.gnome.shell.window-switcher current-workspace-only false
```

---

## Directory Structure

```text
.
├── Assets/                    # Preview screenshots
├── configs/
│   ├── gnome-tweaks/          # GNOME Tweaks config screenshots
│   └── gnome-extensions/      # Per-extension config screenshots
└── README.md
```

| System Path                   | Purpose                  |
|-------------------------------|--------------------------|
| `~/.icons/`                   | Cursor and icon themes   |
| `~/.themes/`                  | GTK themes               |
| `~/.local/share/sounds/`      | Sound themes             |

---

## Credits

- [Yaru Theme](https://github.com/ubuntu/yaru) - The Ubuntu team
- [Distrobox](https://github.com/89luca89/distrobox) - 89luca89
- [Winboat](https://github.com/TibixDev/winboat) - TibixDev
- [Windows 11 Clipboard for Linux](https://github.com/gustavosett/Windows-11-Clipboard-History-For-Linux) - gustavosett
- [Add Water](https://flathub.org/apps/dev.qwery.AddWater) - Flathub
- [Zen Browser](https://zen-browser.app)
- [GNOME Extensions](https://extensions.gnome.org)
- [Felipe Juan's dotfiles](https://github.com/felipe-juan/dotfiles) - README structure inspiration

---

<div align="center">

**Fedorix** is a collaborative effort by **Naitik** and **Khushi**.<br>
*Built through a lot of trial, tweaks, and constant iteration.*

*Star the Repo, Thanks!*

</div>
