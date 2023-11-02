# ftb-revelation
Feed The Beast Revelation modpack
made by Feed The Beast at https://feed-the-beast.com

NOTE: World reset is required when upgrading from v1/v2 to v3.0.1 or higher.

Modpack for Minecraft 1.12.2 with Log4jPatcher.</br>
Revelation is a general all-purpose pack that is designed for solo play as well as small and medium population servers.
This pack contains a mix of magic, tech and exploration mods, and is the largest pack ever built and released by the Feed The Beast Team.

<img src="https://apps.modpacks.ch/modpacks/art/7/revelation.png" width="338" height="338">

NOTE: In compliance with Mojang "End User License Agreement", you will need to agree to the EULA in order to run your own Minecraft server. By using this container you acknowledge the EULA! If you do not agree, then you are not permitted to use this container!
https://account.mojang.com/documents/minecraft_eula

The worldname must be the default "world". 
Settings will reset when upgrading.
Access the console to op and whitelist.

Running ftb-revelation data container:
<code>docker run --name [name of your data container] jonasbonno/ftb-revelation echo 'Data-only container'</code>

Running ftb-revelation server:
<code>docker run --tty=true --interactive=true --detach=true --name [name of your container] --volumes-from [name of your data container] --publish=[port on your host]:25565 jonasbonno/ftb-revelation</code>

When upgrading sometime items have been remove and therefor you have to confirm removal. </br>
To do so run <code>docker attach [name of your container]</code> and type <code>/fml confirm</code> when prompted to confirm or cancel. </br>
Exit with CTRL+P CTRL+Q. </br>

To access the console:
</br><code>docker attach [name of container]</code>
</br>Run your commands
</br>To exit: CTRL+P CTRL+Q

Tips:
</br>Check for OS updates: <code>docker exec -u 0 -it [name of your container] /usr/bin/apt update</code>
</br>Install OS updates: <code>docker exec -u 0 -it [name of your container] /usr/bin/apt full-upgrade -y</code>
</br>Download file: <code>docker cp [name of your container]:/minecraft/options.txt .</code>
</br>Upload file: <code>docker cp options.txt [name of your container]:/minecraft/options.txt</code>
</br>Say Hi!: <code>echo "say Hi!" | socat EXEC:"docker attach [name of your container]",pty STDIN</code>
</br>Say CPU and RAM usage: <code>echo "say $(docker stats [name of your container] --no-stream --format "table CPU: {{.CPUPerc}} RAM: {{.MemPerc}}" | sed -n -e 2p)" | socat EXEC:"docker attach [name of your container]",pty STDIN</code>

The first time the server starts it creates the server.properties file with default settings and spawns "world". 
Not recommended to change these settings by hand.

When upgrading: World reset is required when upgrading from v1/v2 to v3.0.1 or higher.
