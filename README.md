# Minecraft Server Packages

Example packages for a minecraft server. Make sure you already have a playpen network coordinator and 
local coordinator (plus the CLI) setup before following this tutorial. The local coordinator must define the "memory" resource
and the "java-8" attribute.

## Usage

Download spigot and copy the jar over to the spigot-jar folder. Make sure it is named "spigot.jar" exactly.

Copy the sample-server directory and edit the package.json file as you like, and add worlds, plugins, etc.

Run the playpen packaging tool on all folders:

    playpen-p3 pack spigot-common
	playpen-p3 pack spigot-jar
	playpen-p3 pack my-server

This should create a series of p3 files in the current directory. You may now upload them to a playpen
installation using the playpen cli:

    playpen-cli upload *.p3

## Provisioning

To provision a server (assuming you called your server package "my-server"), run this command:

    playpen-cli provision my-server version 1.0 port 25565

You may override anything defined in any package's "strings" section with this command. If you
want to be able to omit the "version" property, run this command:

    playpen-cli promote my-server 1.0

You may then omit the "version 1.0" property when provisioning. The general format for the provision
command is as follows:

    playpen-cli provision <package> [key] [value] [key] [value]...

Some keys, such as "version" and "coordinator" have special meaning, but all other keys will be set
as the server's properties.
