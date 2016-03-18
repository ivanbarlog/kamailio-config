# kamailio-config

This repository contains config files for kamailio. The approach of configuration files is to configure SIP communication so two UAs are able to communicate through 2 insances of kamailio (`kamailioA` and `kamailioB`).

In order to make this configuraiton work you need to specify two constants on each kamailio instance - I suggest to define these constants in `kamailio-local.cfg` eg.:

```
# kamailio-local.cfg for kamailioA

#!define NEXT_HOP_IP "192.168.0.32"
#!define NEXT_HOP_PORT 5060

```

```
# kamailio-local.cfg for kamailioB

#!define NEXT_HOP_IP "192.168.0.31"
#!define NEXT_HOP_PORT 5060
```

This way kamailio forwards all messages from kamailioA that are meant to be sent to the kamailioB to it's address and port and vice versa. The configuration file also contains configuration of registrar service on kamailioA and persistence of UAs' location on kamailioB so the SIP messages can be forwarded successfully.
