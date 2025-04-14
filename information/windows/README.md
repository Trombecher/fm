# Font Management On Windows

## Existing Ways To Install Fonts

### Install Via File Explorer

1. Right-click on target font file.
2. Select option either
    * to install for the current user or
    * the administrator option to install for all users.

### Install Via Microsoft Store

TODO

### Install Via Control Panel (deprecated?)

TODO

### Install Via Settings (preferred)

TODO

## Accepted Font Formats

* OpenType: `.ttf` or `.otf`
* OpenType collection: `.ttc` or `.otc`
* Windows Font-File Format: `.fon` ([specification](#specifications))

## FS Paths

* System (global) fonts folder: `C:\Windows\Fonts`
* User fonts folder: `C:\Users\<USER>\AppData\Local\Microsoft\Windows\Fonts`

## Registry Keys

### System (Global) Font Registration

* Key: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Fonts`
* Format:
  * `Name` (for TrueType font files): `<FONT_NAME> (TrueType)` 
  * `Name` (for `.fon` font files): `<FONT_NAME> (All res)`
  * `Name` (for `.fon` font files): `<FONT_NAME> (120)`
  * `Name` (for `.fon` font files): `<FONT_NAME>`
  * `Type`: `REG_SZ` (string)
  * `Data`: `<FILE_NAME_WITH_EXTENSION>` (in system's font folder)

Note: it seems to work without a suffix but there are sources that suggest adding it.

### System (Global) Font Aliases

* Key: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\FontSubstitures`
* Format:
  * `Name`: `<FONT_NAME>`, sometimes with `,<INT>` suffix (?)
  * `Type`: `REG_SZ` (string)
  * `Data`: `<FONT_NAME>`, sometimes with `,<INT>` suffix (?)

### User Font Registration

* Key: `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Fonts`

### Undocumented Keys

* `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\FontMapperFamilyFallback`
* `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\FontMapper`
  * `\FamilyDefaults` (legacy?)
* `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\FontLink`
  * `\SystemLink`
* `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\FontIntensityCorrection`
* `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\FontDPI`
* `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Font Management`
* `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Font Drivers`

* `HKEY_CURRENT_USER\Software\Microsoft\Windows NT\CurrentVersion\Font Management` (empty?)

## Font Cache

* Service name: "Windows Font Cache Service" (local service)
* Service data path: `C:\Windows\ServiceProfiles\LocalService\AppData\Local\FontCache`
* Font cache file (?): `C:\Windows\System32\FNTCACHE.DAT`

## Sources / Links

* "How to delete Windows 10 system fonts for real, not just remove registry references to them": https://jackyan.com/blog/2020/08/how-to-delete-windows-10-system-fonts-for-real-not-just-remove-registry-references-to-them/
* Microsoft Registry Docs "Windows registry information for advanced users": https://learn.microsoft.com/en-us/troubleshoot/windows-server/performance/windows-registry-advanced-users
* "How to Fix Corrupted Fonts on Windows 10 and 8": https://appuals.com/fix-corrupted-fonts-on-windows-10/
* Microsoft ClearType PDF: https://learn.microsoft.com/en-us/typography/cleartype/pdfs/nowreadthis.pdf
* Windows Internals Blog: https://helgeklein.com/blog/category/windows-internals/
  * https://helgeklein.com/blog/how-the-app-paths-registry-key-makes-windows-both-faster-and-safer/
* Windows Internals Depot: https://empyreal96.github.io/nt-info-depot/
  * Windows Internals PDF (paper-ish): https://empyreal96.github.io/nt-info-depot/Windows-Internals-PDFs/Windows%20System%20Internals%207e%20Part%201.pdf
* Temporarily adding fonts "AddFontResourceW function (wingdi.h)": https://learn.microsoft.com/en-us/windows/win32/api/wingdi/nf-wingdi-addfontresourcew
* Windows font paths "How to find all fonts paths on Windows": https://stackoverflow.com/questions/66929898/how-to-find-all-fonts-paths-on-windows
* (Legacy) MS docs on "Add a font": https://support.microsoft.com/en-us/office/add-a-font-b7c5f17c-4426-4b53-967f-455339c564c1#:~:text=All%20fonts%20are%20stored%20in,files%20folder%20into%20this%20folder.
* "Installing additional fonts": https://infosys.beckhoff.com/english.php?content=../content/1033/sw_os/7137826187.html&id=
* "Installing Fonts with Group Policy and MSIs": https://deployhappiness.com/installing-fonts-with-group-policy/
* Install fonts via gp: https://community.spiceworks.com/t/install-fonts-via-gpo/150594/22
* HKLM unofficial documentation: https://renenyffenegger.ch/notes/Windows/registry/tree/HKEY_LOCAL_MACHINE/Software/Microsoft/Windows-NT/CurrentVersion/index

### "Change Default Font" Tutorials

* https://www.buildwindows.com/change-windows-font/
* https://www.youtube.com/watch?v=6istx0pwgpc

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