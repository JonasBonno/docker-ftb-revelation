# ftb-revelation - v1.2.0
Feed The Beast Revelation modpack
made by Feed The Beast at https://feed-the-beast.com

Modpack for Minecraft 1.12.2.
Revelation is a general all-purpose pack that is designed for solo play as well as small and medium population servers.
This pack contains a mix of magic, tech and exploration mods, and is the largest pack ever built and released by the Feed The Beast Team.

<img src="https://media-elerium.cursecdn.com/avatars/134/670/636493650464216291.png" width="338" height="338">

NOTE: In compliance with Mojang "End User License Agreement", you will need to agree to the EULA in order to run your own Minecraft server. By using this container you acknowledge the EULA! If you do not agree, then you are not permitted to use this container!
https://account.mojang.com/documents/minecraft_eula

This Dockerfile will always download latest build of Feed The Beast Revelation when building.
The releases on hub.docker.com are build when a new stable release is available from Feed The Beast.

The worldname must be the default "world". 
Settings will reset when upgrading.
Access the console to op and whitelist.

Running ftb-revelation data container:
docker run --name [name of your data container] jonasbonno/ftb-revelation:1.2.0 echo 'Data-only container'

Running ftb-revelation server:
docker run --tty=true --interactive=true --detach=true --name=[name of your container] --volumes-from [name of your data container] --publish=[port on your host]:25565 jonasbonno/ftb-revelation:1.2.0

When upgrading sometime items have been remove and therefor you have to confirm removal. </br>
To do so run "docker attach [name of your container]" and type "/fml confirm" when prompted to confirm or cancel. </br>
Exit with CTRL+P CTRL+Q. </br>

To access the console:
</br>docker attach [name of container]
</br>Run your commands
</br>To exit: CTRL+P CTRL+Q

The first time the server starts it creates the server.properties file with default settings and spawns "world". 
Not recommended to change these settings be hand.

When upgrading:
To upgrade delete ftb-revelation server and start new ftb-revelation server with --volumes-from [name of your data container].
Settings will reset when upgrading.
Access the console to op and whitelist.
