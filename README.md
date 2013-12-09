check_minecraft
===============

Nagios plugin to check the status of minecraft servers

DESCRIPTION
===============
Attempts to connect to a minecraft server on the specified host:port.
After connecting, a server ping packet that corresponds to the version
of Minecraft specified is created and sent to the server. If the server
responds, the response is decoded to determine the number of players
online, the max number of players, and time taken to complete the
process.

If the :port is not specified, the default port number of 25565 will be
used.

OPTIONS
===============
-?  Display this documentation.

-V  Version of the minecraft server to be checked [required]
    15 - Minecraft version 1.5.x
    16 - Minecraft version 1.6.x
    17 - Minecraft version 1.7.x

-P  TCP port to connect to the server. Defaults to 25565 [optional]
-H  Hostname or IP of the minecraft server [required]

