# Use the official OpenJDK 17 image as base
FROM openjdk:19-jdk-alpine

# Define the working directory
WORKDIR /minecraft-server

# Expose the necessary port
EXPOSE 25565

# COPY MAP FOLDERS
COPY ../spigot/.map/world /minecraft-server
COPY ../spigot/.map/world_nether /minecraft-server
COPY ../spigot/.map/world_the_end /minecraft-server

# SERVER PROPERTIES
COPY server.properties /minecraft-server
COPY whitelist.json /minecraft-server

# COPY END USER LICENCE AGREEMENT
COPY eula.txt /minecraft-server

# ENABLE END USER LICENCE AGREEMENT IN THE SERVER
RUN echo "eula=true" > eula.txt

# DOWNLOAD MINECRAFT SERVER 1.20.1 JAR
RUN wget -O minecraft_server.jar https://launcher.mojang.com/v1/objects/84194a2f286ef7c14ed7ce0090dba59902951553/server.jar

# LAUNCH THE SERVER
ENTRYPOINT ["java", "-Xmx1024M", "-Xms1024M", "-jar", "minecraft_server.jar", "nogui"]
