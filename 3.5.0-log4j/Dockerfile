FROM openjdk:8-jre

MAINTAINER Jonas Bonno Mikkelsen (https://github.com/JonasBonno)

# Updating container
RUN apt-get update && \
	apt-get install apt-utils --yes && \
	apt-get upgrade --yes --allow-remove-essential && \
	apt-get clean && \
	rm -rf /var/lib/apt/lists/*

# Setting workdir
WORKDIR /minecraft

# Creating user and downloading files
RUN useradd -m -U minecraft && \
	mkdir -p /minecraft/world && \
	wget --no-check-certificate https://api.modpacks.ch/public/modpack/35/2059/server/linux -O serverinstall_35_2059 && \
	chmod u+x serverinstall_* && \
	./serverinstall_* --auto && \
	rm serverinstall_* && \
	echo "#By changing the setting below to TRUE you are indicating your agreement to our EULA (https://account.mojang.com/documents/minecraft_eula)." > eula.txt && \
	echo "$(date)" >> eula.txt && \
	echo "eula=true" >> eula.txt && \
	wget --no-check-certificate https://launcher.mojang.com/v1/objects/02937d122c86ce73319ef9975b58896fc1b491d1/log4j2_112-116.xml -O log4j2_112-116.xml && \
	sed -i 's/-jar/-Dlog4j.configurationFile=log4j2_112-116.xml -jar/g' start.sh && \
	chown -R minecraft:minecraft /minecraft

# Changing user to minecraft
USER minecraft

# Expose port 25565
EXPOSE 25565

# Expose volume
VOLUME ["/minecraft/world"]

# Start server
CMD ["/bin/bash", "/minecraft/start.sh"]
