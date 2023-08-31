---
layout: default
title: Recommend tools/software
parent: Software
---
Written by [slydelv](https://github.com/slydelv), among others. 

Trusted tools. 

> Tool can include program, application, script, web-app, web site, etc.

# General Tools/Toolkits/Multi-tools
* [Windows Repair Toolbox](https://windows-repair-toolbox.com)
* [SophiApp](https://github.com/Sophia-Community/SophiApp)
* [slydelv's toolbox - unfinished](https://github.com/slydelv/windows-ps-toolbox-gui)

# Optimisers / Tweakers
Can be a bit touchy. There's a lot out there. Let's stick to tried & tested.
## Uninstallers (Free)
* [Revo Uninstaller](https://www.revouninstaller.com/) 
  * Tried & Trusted over Time
* [Uninstalr](https://uninstalr.com/)
  * New, has features free Revo doesn't.


# Privacy / Antispy
* [O&O  ShutUp](https://www.oo-software.com/en/shutup10)
  * Antispy tool for Windows 10 and 11
* [Privacy.sexy](https://privacy.sexy/)
  * Web resource / scripts for Multi-OS Privacy

# OS Installation
* [Rufus](https://rufus.ie/en/)
  * Create bootable USB Drives
* [Install Windows without USB](https://github.com/iidanL/InstallWindowsWithoutUSB)
  * Relatively unique way of reinstalling Windows, like a USB reinstall, without a USB.
* [The Oven Forum](https://theoven.org/)
  * Windows Image building and editing forum. Win10XPE, Win10PE, Gena, LiveSystem, MicroWinpeBuilder, etc.
* [Official Windows 10](https://www.microsoft.com/en-gb/software-download/windows10)
* [Official Windows 11](https://www.microsoft.com/en-gb/software-download/windows11)
  * To bypass MS sign in on W11 setup, do not connect to WiFi, press Shift + F10 to open CMD then type `oobe/bypassnro` and restart.

# Modification Tools
* [Ameliorated](https://ameliorated.io/)
  * Massive Windows modification tool/
* [Windhawk](https://ramensoftware.com/windhawk)
  * A "marketplace" for Windows program customisation/

# Package Managers
* [Chocolatey](https://chocolatey.org/)
  * Multi source official and custom package manager
  * Fully automates installs
  * Packages can be pre-customised, ranked & validated
  * Can install to user-space or admin
  * Since packages are fully automated and scripted, can install from any source
  * `Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))`
* [WinGet](https://learn.microsoft.com/en-us/windows/package-manager/winget/)
  * NuGet based package manager - "Linux style".
 * [Winget.run](https://winget.run/)
   * simple package explorer / scriptlet generator
* [Scoop](https://scoop.sh/)
  * Kind of a package manager but not really; a command line installer
  * Installs into user-space
  * Automates installs

# Misc
* [Everything](https://www.voidtools.com/downloads/)
  * Search everything in Windows, instantly. Hotkey support. Live results. Really, really fast. 
  *  `choco install everything /y`
* [AutoHotkey](https://www.autohotkey.com/)
  * GOAT of hotkey implementation, also used for automation. 
* [VisualBCD](https://www.boyans.net/)
  * Graphical, GUI, based BCD Editor. 

# Testing
* [HD Sentinel](https://www.hdsentinel.com/)
  * HDD & SSD monitoring & analysis software
