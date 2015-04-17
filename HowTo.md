# Introduction #

It is possible to obtain the full weupnp API documentation from the [Downloads](http://code.google.com/p/weupnp/downloads/list) section.
The code contained in [Main.java](http://code.google.com/p/weupnp/source/browse/trunk/src/main/java/org/wetorrent/upnp/Main.java) itself shows a lot of the capabilities of the library, and the comments it includes should make it easier to understand how it works.

# Sample code #

```
Logger logger = LogUtils.getLogger();
logger.info("Starting weupnp");

GatewayDiscover discover = new GatewayDiscover();
logger.info("Looking for Gateway Devices");
discover.discover();
GatewayDevice d = discover.getValidGateway();

if (null != d) {
    logger.log(Level.INFO, "Gateway device found.\n{0} ({1})", new Object[]{d.getModelName(), d.getModelDescription()});
} else {
    logger.info("No valid gateway device found.");
    return;
}

InetAddress localAddress = d.getLocalAddress();
logger.log(Level.INFO, "Using local address: {0}", localAddress);
String externalIPAddress = d.getExternalIPAddress();
logger.log(Level.INFO, "External address: {0}", externalIPAddress);
PortMappingEntry portMapping = new PortMappingEntry();

logger.log(Level.INFO, "Attempting to map port {0}", SAMPLE_PORT);
logger.log(Level.INFO, "Querying device to see if mapping for port {0} already exists", SAMPLE_PORT);

if (!d.getSpecificPortMappingEntry(SAMPLE_PORT,"TCP",portMapping)) {
    logger.info("Sending port mapping request");

    if (d.addPortMapping(SAMPLE_PORT,SAMPLE_PORT,localAddress.getHostAddress(),"TCP","test")) {
        logger.log(Level.INFO, "Mapping succesful: waiting {0} seconds before removing mapping.", WAIT_TIME);
        
        Thread.sleep(1000*WAIT_TIME);
        d.deletePortMapping(SAMPLE_PORT,"TCP");

        logger.info("Port mapping removed");
        logger.info("Test SUCCESSFUL");
    } else {
        logger.info("Port mapping removal failed");
        logger.info("Test FAILED");
    }
    
} else {
    logger.info("Port was already mapped. Aborting test.");
}

logger.info("Stopping weupnp");
```