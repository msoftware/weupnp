# Source code #
The source code for this library is now hosted on GitHub at https://github.com/bitletorg/weupnp


---


## Overview ##
Weupnp is a lightweight Java library, released under the LGPL licence, designed to implement the [UPnP protocol](http://en.wikipedia.org/wiki/Universal_Plug_and_Play) to handle port mappings on Gateway Devices.

## Usages ##
  * Weupnp is used by the [BitLet applet](http://www.bitlet.org/) to open ports for incoming connections and to build an [interactive console](http://www.bitlet.org/upnp) for the administration of port mappings on UPnP devices.
  * Since version 1.6, the [UPnP PortMapper](http://upnp-portmapper.sourceforge.net/) can use weupnp to communicate with Gateway Devices.
  * [Jitsi](http://www.jitsi.org/) (formerly SIP communicator) uses weupnp to gather UPnP candidates for ICE operations

See [here](HowTo.md) how to use weupnp in your own project.

## Acknowledgements ##
The implementation of weupnp was inspired by [miniupnp](http://miniupnp.free.fr/), a C UPnP library by Thomas Bernard.

## Participate ##
If you wish to contribute, feel free to drop a line to _daniele.castagna_ and _ale.bahgat_ (both at gmail.com).