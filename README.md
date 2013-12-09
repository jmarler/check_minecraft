check_minecraft
===============

Nagios plugin to check the status of minecraft servers.  Supports 
Minecraft 1.5, 1.6, and 1.7.  Tested on MCPC+, Spigot, CraftBukkit, 
and Vanilla servers

Description
-------------------------
Attempts to connect to a minecraft server on the specified host:port.
After connecting, a server ping packet that corresponds to the version
of Minecraft specified is created and sent to the server. If the server
responds, the response is decoded to determine the number of players
online, the max number of players, and time taken to complete the
process.

If the port is not specified, the default port number of 25565 will be
used.

Options
-------------------------
-?  Display this documentation.
<P>
-V  Version of the minecraft server to be checked **[required]**<BR>
&nbsp;&nbsp;&nbsp;15 - Minecraft version 1.5.x<BR>
&nbsp;&nbsp;&nbsp;16 - Minecraft version 1.6.x<BR>
&nbsp;&nbsp;&nbsp;17 - Minecraft version 1.7.x

-P  TCP port to connect to the server. Defaults to 25565 [optional]
<P>
-H  Hostname or IP of the minecraft server **[required]**

Command-Line Example
-------------------------

    $ ./check_minecraft -H localhost -V 17
    MINECRAFT SERVER READY - 0/100 online|0.219s

Nagios configuration examples
-------------------------

    define command{
	    command_name	check_minecraft
	    command_line	/usr/lib/nagios/plugins/check_minecraft -H $ARG1$ -V $ARG2$
	    }
	
    # Minecraft 1.5 Server Ping Check
    define service{
        hostgroup_name                  minecraft-15-servers
        service_description             Minecraft 1.5
        check_command                   check_minecraft!$HOSTADDRESS$!15
        use                             generic-service
        notification_interval           5 ; set > 0 if you want to be renotified
    }
    
    # Minecraft 1.6 Server Ping Check
    define service{
        hostgroup_name                  minecraft-16-servers
        service_description             Minecraft 1.6
        check_command                   check_minecraft!$HOSTADDRESS$!16
        use                             generic-service
        notification_interval           5 ; set > 0 if you want to be renotified
    }
    
    # Minecraft 1.7 Server Ping Check
    define service{
        hostgroup_name                  minecraft-17-servers
        service_description             Minecraft 1.7
        check_command                   check_minecraft!$HOSTADDRESS$!17
        use                             generic-service
        notification_interval           5 ; set > 0 if you want to be renotified
    }


