

# What you'll need #

  * An SVN client - such as [TortoiseSVN](http://tortoisesvn.tigris.org/) for Windows.
  * The Mozilla source code - get it [here](https://developer.mozilla.org/en/Mozilla_Source_Code_(HTTP%2f%2fFTP)).
  * Microsoft's Visual Studio - I used VS 2008.

Optionally, to sign XPIs and updates:
  * [McCoy](https://developer.mozilla.org/En/McCoy)
  * Network Security Services (NSS) - from the [NSS Mozilla FTP site](ftp://ftp.mozilla.org/pub/mozilla.org/security/nss/releases/), make sure you get the Windows package.
  * Netscape Portable Runtime (NPR) - from the [NPR Mozilla FTP site](http://ftp.mozilla.org/pub/mozilla.org/nspr/releases/), make sure you get the Windows package.
  * Microsoft's [tool](http://www.microsoft.com/downloads/details.aspx?familyid=F9992C94-B129-46BC-B240-414BDFF679A7&displaylang=en) to import PVK files - pvkimprt.exe

# Compiling the source #

  * Head over to [the sources repository](http://code.google.com/p/ff-activex-host/source/checkout) and follow the guidelines to check out a copy of the code from the SVN repository.
  * I placed the Mozilla sources in c:\src\mozilla, you will need to change the include directories of the project if you places the sources in a different location.
  * The 'easiest' way to get all the include files is to actually build the Mozilla sources, which is not that easy, but follow [this guide](https://developer.mozilla.org/en/Build_Documentation).
  * Build the plugin.

# To sign the XPI #

Useful articles about signing XPIs:

  * https://developer.mozilla.org/En/Signing_a_XPI
  * http://oyoy.eu/huh/firefox-extension-code-signed-with-spc-pvk/

Important:

  * 7z cannot created signed XPIs. It's good enough for unsigned XPIs, but it will not be able to create proper signed XPIs.

## Signing ##
Create the directory structure you desire under a folder named 'signed'
```
c:\tools\nss-3.9\bin\signtool.exe -d <certificate-path> -k <certificate-nickname> -p <password> signed
```

## Creating the XPI ##
From within the 'signed' folder execute:
```
c:\mozilla-build\info-zip\zip <XPI-name> META-INF\zigbert.rsa
c:\mozilla-build\info-zip\zip -r -D <XPI-name> * -x META-INF\zigbert.rsa
```