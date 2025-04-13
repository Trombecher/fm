# Everything about fonts

## Existing Ways To Install Fonts

### Install Via File Explorer

1. Right-click on target font file.
2. Select option either
    * to install for the current user or
    * the administrator option to install for all users.

### Install Via Microsoft Store

### Install Via Control Panel (deprecated?)

### Install Via Settings (preferred)

## Accepted Font Formats

* OpenType: `.ttf` or `.otf`
* OpenType collection: `.ttc` or `.otc`
* Windows Font-File Format: `.fon` ([specification](#specifications))

## FS Paths

* System (global) fonts folder: `C:\Windows\Fonts`
* User fonts folder: `C:\Users\<USER>\AppData\Local\Microsoft\Windows\Fonts`

## Registry Keys

* System (global) font registration: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Fonts`
* System (global) font aliases: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\FontSubstitures`
* User font registration: `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Fonts`

## Font Cache

* Service name: "Windows Font Cache Service" (local service)
* Service data path: `C:\Windows\ServiceProfiles\LocalService\AppData\Local\FontCache`
* Font cache file (?): `C:\Windows\System32\FNTCACHE.DAT`

## Sources / Links

* "How to Fix Corrupted Fonts on Windows 10 and 8": https://appuals.com/fix-corrupted-fonts-on-windows-10/
* Microsoft ClearType PDF: https://learn.microsoft.com/en-us/typography/cleartype/pdfs/nowreadthis.pdf
* Windows Internals Blog: https://helgeklein.com/blog/category/windows-internals/
  * https://helgeklein.com/blog/how-the-app-paths-registry-key-makes-windows-both-faster-and-safer/
* Windows Internals Depot: https://empyreal96.github.io/nt-info-depot/
  * Windows Internals PDF (paper-ish): https://empyreal96.github.io/nt-info-depot/Windows-Internals-PDFs/Windows%20System%20Internals%207e%20Part%201.pdf
* Temporarily adding fonts "AddFontResourceW function (wingdi.h)": https://learn.microsoft.com/en-us/windows/win32/api/wingdi/nf-wingdi-addfontresourcew
* Windows font paths "How to find all fonts paths on Windows": https://stackoverflow.com/questions/66929898/how-to-find-all-fonts-paths-on-windows
* (Legacy) MS docs on "Add a font": https://support.microsoft.com/en-us/office/add-a-font-b7c5f17c-4426-4b53-967f-455339c564c1#:~:text=All%20fonts%20are%20stored%20in,files%20folder%20into%20this%20folder.

### Discussions

* PowerToys GH Issue "Adjust how fonts render in Windows": https://github.com/microsoft/PowerToys/issues/6918
* DirectWrite API proposal to open source: https://github.com/microsoft/WindowsAppSDK/issues/112

### StackOverflow

* "How to get all installed font path/filename on Windows?": https://stackoverflow.com/questions/73475622/how-to-get-all-installed-font-path-filename-on-windows?noredirect=1&lq=1
* "Where are user specific font files stored?": https://superuser.com/questions/1597642/where-are-user-specific-font-files-stored
* "OpenType fonts in the Windows Registry": https://stackoverflow.com/questions/61248375/opentype-fonts-in-the-windows-registry

### Specifications

* Windows Font-File specification: https://web.archive.org/web/20080115184921/http://support.microsoft.com/kb/65123
* Microsoft Typography (includes OpenType and TrueType specs): https://learn.microsoft.com/en-us/typography/about

### Font Libraries

* https://github.com/fontmatrix/fontmatrix
* https://github.com/foliojs/font-manager
* https://github.com/r-lib/systemfonts/blob/main/src/win/FontManagerWindows.cpp
* https://www.fileerrors.com/hkey-local-machine-software-microsoft-windows-nt-currentversion-fonts.html
* https://github.com/moi15moi/FindSystemFontsFilename/blob/main/find_system_fonts_filename/windows/windows_fonts.py