I am not longer able to continue maintaining this code. I have migrated the repository to [GitHub](https://github.com/leeor/ff-activex-host), in hopes of making it easier for individuals interested in this work to continue using/improving it.


# What is it? #
This Firefox plugin makes it possible to use (host) ActiveX controls in Firefox. It is based on the Gecko NPAPI and provides full access to the hosted control (events, functions, properties).

Security-wise, the plugin checks whether the control is safe for scripting and that it has not been marked as unsafe by IE (kill bits).

# Who is it for? #
The intended crowd of this plugin are web application developers who need to embed into their application content that requires native code, and (1) already have an ActiveX control that fulfills their needs, or (2) don't enjoy writing the same code twice and want to reuse the same piece of code in Firefox and IE.

# How do I use it? #
The plugin registers its own MIME Type - meaning that currently web pages need to be written with this plugin in mind. It does not work transparently in sites that use ActiveX objects.

That said, you can go to the downloads section and download an XPI with this plugin. Notice that the packaged XPI contains a plugin that is not site locked to a specific domain - so do take care, and don't come here blaming me later on ;-)

Full documentation is [here](Documentation.md).

# Security #
The plugin has some security related features to limit the risk it might pose to users by making ActiveX controls available in Firefox. First of all, it is using a special MIME Type so that it won't get triggered by sites that were not specifically designed for it. Additionally, it supports lists of well known CLSIDs and PROGIDs so that it can be limited to use with specific controls and interfaces. Finally, it can be "site locked" to make sure it's only being used by a predetermined list of domains.

A derived project, http://code.google.com/p/np-activex/, provides additional scripts that enable Chrome users to use ActiveX objects without additional changes to the HTML/JavaScript.

# Usage Sample #
This HTML Object will use the Shockwave Flash ActiveX (not the FF plugin) to embed a movie in an HTML page. (Note that both a _clsid_ and a _progid_ are given, but only one of them is needed)
```
	<object
		id="Control"
		TYPE="application/x-itst-activex"
		ALIGN="baseline" BORDER="0"
		WIDTH="300" HEIGHT="300"
		clsid="{D27CDB6E-AE6D-11cf-96B8-444553540000}"
		progid="ShockwaveFlash.ShockwaveFlash"
		event_OnReadyStateChange="OnReady"
		param_src="http://www.youtube.com/v/53RdNYwImYc">
	</object>
```

# Author #
Developed by Leeor Aharon, at [CloudShare Ltd](http://www.cloudshare.com).