# Introduction #
Build instructions for FF ActiveX with Firefox 3.6++

## Download ##
```
hg clone https://ff-activex-host.googlecode.com/hg/ ff-activex-host  
hg clone http://hg.mozilla.org/releases/mozilla-1.9.2/ c:\src\mozilla
```

  * Download http://ftp.mozilla.org/pub/mozilla.org/mozilla/libraries/win32/MozillaBuildSetup-1.4.exe
  * Install it


## Mozilla Build ##
Install Mozilla Build into c:\mozilla-build

## Create c:\src\mozilla\.mozconfig ##
```
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/objdir
ac_add_options --enable-application=browser
mk_add_options MOZ_CO_PROJECT=browser
```

## Build Mozilla ##
```
start-msvc9.bat
make -f client.mk
```