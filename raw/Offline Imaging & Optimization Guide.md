# LTSC 2019 x64 - Offline Imaging & Optimization Guide (Updated: 2019-07-17)

-> **aka. creating your own perfect, debloated LTSC 2019 x64 .iso image distribution** <-
![boomer](https://s.put.re/cQgD9t78.png)

_Prerequisites for offline imaging and optimization_:

- A machine with any Windows 10 1607+ edition
- Appropriate [Windows ADK](https://docs.microsoft.com/en-us/windows-hardware/get-started/adk-install?ocid=tia-235208000) version installed for your Windows 10 build (optional, but **highly recommended** - needed for W10UI .iso creation)
  _(however if you refuse to install the ADK, you can try to play with [DISM and Oscdimg files](https://m.put.re/U86hXhYo.zip) which i've extracted from Windows 10 1809 ADK directly)_

## 1. Creating updated .iso image based on the original LTSC 2019 x64:

Download the originally released LTSC 2019 x64 Volume .iso from MVS (My Visual Studio) (build 17763.1) [EVAL](https://software-download.microsoft.com/download/pr/17763.1.180914-1434.rs5_release_CLIENT_LTSC_EVAL_x64FRE_en-us.iso) + [SVF Repo with 38 Languages](https://mega.nz/#F!rUkiGapC!HkzkUIEjkqmUkSyqVeFsbQ) ([Source](https://forums.mydigitallife.net/threads/windows-10-svf-repository.63324/page-128#post-1468363)).

The SVF .exe patch will rebuild the **original** Volume .iso image using the **original** EVAL (Demo) .iso, if you have doubts then you can verify it yourself - compare the Volume image's SHA-1 hash against [this proxy dump with official repo of MVS/MSDN hashes](https://msdn.rg-adguard.net/public.php?seach=Windows+10+Enterprise+LTSC+2019&str=100) (or ask someone with MVS access to check for you, MVS access costs $1,199).

- Place both the EVAL .iso and your language's SVF .exe into the same folder
- Run the .exe as Administrator to rebuild original Volume MVS 17763.1 .iso in your language
- Remove the EVAL .iso and use [7-Zip](https://www.7-zip.org/) ([or WinRAR](https://www.rarlab.com/download.htm)) to extract the contents of the new rebuilt Volume MVS .iso to a folder with the same name as the .iso
- Download the [W10UI tool](https://github.com/abbodi1406/BatUtil/tree/master/W10UI) by [@abbodi1406](https://forums.mydigitallife.net/members/abbodi1406.204274/) (Open-Source), run it as Administrator and point the "Target" to the extracted .iso folder
- Download the newest updates; [here](https://pastebin.com/raw/qLigTaqT) are the current (17763.615) 1809 updates to integrate with W10UI, alternatively use mydigitallife tool called [WHDownloader](https://drive.google.com/file/d/1b4A_qoXkgxAiwSxB2Bqhm03AwFqHVd6X/view) ([Source](https://forums.mydigitallife.net/threads/whdownloader-download.66243/)) in order to always get fresh updates for offline integration ([see this gif as a how-to](https://s.put.re/3Uj8oJJb.gif)), _or_ use [this script](https://github.com/aaronparker/LatestUpdate) (Open-Source).
- Create a new folder called "updates" and put all those update files there, point the "Updates" to this folder in W10UI tool
  It's also recommended to select **.NET 3.5** to pre-integrate and enable **Cleanup System Image** in the tool
- Start the process and wait for a new .iso to be created - it can take quite a long time on older machines, so better go for a vodka while it's running

Follow my W10UI settings as an example:

![screenshot_w10ui](https://s.put.re/eqCfsoba.png)
-> (Open image in a new browser tab to enlarge) <-

## 2. Optimizing, tweaking and debloating the updated .iso image (new method):

_The old method is still [available here](https://rentry.co/ltsc_optimize_old) if you prefer it, but i don't support it anymore._

**New method:**

Download the **[Optimize-LTSC](https://m.put.re/8Nv1Fb41.zip)** script (Open-Source) - it's essentially an **[Optimize-Offline](https://github.com/DrEmpiricism/Optimize-Offline)** script forked by me - as the name suggests, my fork is designed for LTSC.

**Changes:**

- Useless integrations have been removed: Edge, Dedup, DaRT, Win32Calc
- Script has been fully debugged - i have found some registry mistakes that the original author didn't notice and corrected them myself
- The script has a two new _optional_ switches enabled by default (edit the `Start.cmd` file and remove the switches if don't want them):
  `-DisableUAC` - this switch disables UAC and LUA in the offline image's registry hives - it will grant the user Full Administrator Permissions
  `-Win7GUI` - this switch changes some of the default Windows 10 GUI elements into those of Windows 7 (more details in the `.ps1` file)
  _if you use it, then it's also highly recommended to install StartIsBack++ and OldNewExplorer from the end of this paste_
- SetupComplete.cmd files and scripts integration function has been updated, so you no longer have to edit it manually
- A generic, custom _unattend.xml_ file is included and will be integrated to the offline image (remove from `\Resources\Additional\Unattend\` if you don't want it):
  -Local Account by Default (skipped Online Account creation)
  -Privacy settings are skipped in the OOBE
  -Sending installation report to the Microsoft is disabled
- [KMS_VL_ALL](https://pastebin.com/cpdmr6HZ) by [@abbodi1406](https://forums.mydigitallife.net/threads/kms_vl_all-smart-activation-script.79535/) is now applied to the SetupComplete.cmd script by default, so your LTSC 2019 x64 installation will automatically activate (remove the files from the `\Resources\Additional\Setup\` folder if you prefer to activate manually instead)
- Added more registry tweaks to disable even more telemetry options + annoyances and to block Windows Telemetry IPs in the Firewall.

**Best Practices:**

- Make sure to place your **Optimize-LTSC** folder in a short path like `C:\Optimize-LTSC\` (long paths are not supported and will cause serious errors)
- Test every single optimized image on a VM firstly before installing it on a real machine.

The script removes Provisioned Application Packages in a [safe and proper way](https://s.put.re/ntniATZA.png), so the installed OS will remain sfc perfect, it also applies registry tweaks to the offline registry hives in order to disable all the possible telemetry & to enhance aesthetics + usability of the system.

**If you want to integrate your own scripts and files to apply/install with the Windows Setup together using the Optimize-LTSC's SetupComplete.cmd file - [check out my supplementary minor guide](https://rentry.co/optimize-ltsc_setupcomplete).**

It's **highly recommended** _(but not necessary anymore with my fork)_ to edit the .ps1 file yourself - at least basic PowerShell knowledge is required to edit more advanced parts of the script, however even if you're a noob you still should be able to at least review the registry section easily; add your own registry tweaks, remove existing ones you don't like, etc.

- [here's a short tip how to do that](https://pastebin.com/raw/4wyuNGwc)

Edit the Optimize-LTSC's **Start.cmd** file and point it to your new W10UI updated .iso image, afterwards run **Start.cmd** as Administrator:

![screenshot_optimize-ltsc_cmd](https://s.put.re/5XXg9Uim.png)
-> (Open image in a new browser tab to enlarge) <-
NOTE: If for whatever reason you want to integrate the **Store** app to LTSC 2019 x64, then you have to add the `-WindowsStore` parameter right after the `-Features` parameter, it's also **not** recommended to remove any Xbox-related system apps if you're integrating the Store!

_In the Optimize-LTSC GUI windows, you have to press & hold the **left Ctrl** button on your keyboard while clicking on the values with left mouse button_

[Here's the list of the Windows Apps that are completely safe (and recommended) to remove with Optimize-LTSC:](https://s.put.re/agHjCBvz.png)

- BioEnrollment (remove only if you're **not** going to use any biometric sensors like fingerprint readers or camera's face recognition)
- ECApp (another app related to biometrics)
- LockApp (it's the Lock Screen which you have to move with the mouse cursor, it's a crap for tablets and other touch screen devices, completely useless and safe to remove, the true Login Screen will remain intact)
- MicrosoftEdgeDevToolsClient (app related to Microsoft Edge browser, useless and safe to remove since there's no Edge on LTSC 2019)
- Win32WebViewHost (same as above, useless)
- ContentDeliveryManager (this app is used by Microsoft to push the _sponsored_ content to the end users; it is responsible for automatic Start Menu pinning of the 3rd party apps shortcuts, such as "Candy Crush Soda Saga" and other bloatware)
- ParentalControls (just as the name suggests, bloat, safe to remove)
- PeopleExperienceHost (it's the "People" icon on the taskbar, useless and safe to remove)
- SecHealthUI (Windows Defender - highly recommended to remove if you're going to install a third party AV suite, like ESET or Kaspersky)
- XboxGameCallableUI _and_ XGpuEjectDialog (remove them only if you hate Full Screen Optimization and Xbox Game Bar, Game DVR, do not remove if you integrate the Store app)

[Here's the list of Windows Capability Packages that are safe (and recommended) to remove:](https://s.put.re/hUB1q77Y.png)

- App.Support.QuickAssist
- Hello.Face.17658
- Hello.Face.Migration.17658
- MathRecognizer
- OneCoreUAP.OneSync

_Don't remove Internet Explorer and Windows Media Player - a lot of Games and Programs use the IE engine infrastructure and WMP codecs._

[Here's the list of Windows Features recommended to **disable**:](https://s.put.re/mQs7j4z5.png)

- Printing-XPSServices-Features
- WorkFolders-Client
- FaxServicesClientPackage

[Here's the list of Windows Features recommended to **enable**:](https://s.put.re/TXWtbDxb.png)

- LegacyComponents
- DirectPlay
- Microsoft-Windows-Subsystem-Linux (Optionally, if you need it)

## 3. Creating bootable media for clean installation:

It's recommended to select **Solid** compression at the end stage of Optimize-LTSC script, and after it creates a new .iso what you want to do is to use [Rufus](https://rufus.ie/) in order to create a bootable USB; in the Rufus you should choose:

- GPT for UEFI {FAT32}
  _or_
- MBR for legacy BIOS {NTFS}

It's also recommended to disable **Fast Boot** in the UEFI/BIOS for the time of installation.

_Also, for your information: a properly offline-optimized LTSC 2019 x64 **can be** updated normally through Windows Update and the removed components **will not return with the updates**._

## 4. What to do after clean installation:

- **If you want to make your LTSC 2019 x64 look more like Windows 7:**
  -download [OldNewExplorer v1.1.8.4](https://tihiy.net/files/OldNewExplorer.rar) ([Source](https://msfn.org/board/topic/170375-oldnewexplorer-118/)), unpack it to `C:\Program Files\OldNewExplorer\` and set it up with [those settings](https://s.put.re/kxrEnG6L.png)
  -download [StartIsBack++ v2.8.6](https://s.put.re/NbaNMWrh.6_p.exe) ([Source](https://www.nsaneforums.com/topic/347353-startisback-286/?tab=comments#comment-1484008)) - it's a _pre-activated_ installer made by nsaneforums.com's trusted member [FoRMaT](https://www.nsaneforums.com/profile/93205-format/), install it (choose [Install for everyone](https://s.put.re/7oaDhmVu.png)), then go to the StartIsBack++ settings and [disable Auto Updates](https://s.put.re/mC56cKpz.png), also [check this tickbox](https://s.put.re/TKsazXts.png) and Apply
  -Reboot Windows afterwards

Good luck anons!

This guide will be consistently updated - write in the official, current /fwt/ thread on /g/ if you have any suggestions or questions.

**Remember to not be a fool and always verify checksums/hashes of everything, also avoid downloading _homebrew_ .iso images from shady sources - i've created this guide to teach you how to do it yourself.**

[Here's the original /fwt/ paste](https://rentry.co/fwt), and [here's the current /fwt/ thread on /g/](http://boards.4channel.org/g/thread/71925721)
