FROM openjdk:17-jdk-alpine

WORKDIR /minecraft-server

EXPOSE 25565

# COPY MAP FOLDERS
COPY ./.map/world /minecraft-server
COPY ./.map/world_nether /minecraft-server
COPY ./.map/world_the_end /minecraft-server

# SERVER PROPERTIES
COPY ./server.properties /minecraft-server
COPY ./whitelist.json /minecraft-server

# COPY END USER LICENCE AGREEMENT
COPY ./eula.txt /minecraft-server

# ENABLE END USER LICENCE AGREEMENT IN THE SERVER
RUN echo "eula=true" > eula.txt

# DOWNLOAD MINECRAFT SERVER 1.20.1 JAR
RUN wget -O minecraft_server.jar https://launcher.mojang.com/v1/objects/84194a2f286ef7c14ed7ce0090dba59902951553/server.jar

# LAUNCH THE SERVER
ENTRYPOINT ["java", "-Xmx1024M", "-Xms1024M", "-jar", "minecraft_server.jar", "nogui"]
