FROM openjdk:17-jdk-alpine

WORKDIR /minecraft-server

EXPOSE 25565

COPY ./.map/world /minecraft-server
COPY ./.map/world_nether /minecraft-server
COPY ./.map/world_the_end /minecraft-server
COPY ./eula.txt /minecraft-server


RUN echo "eula=true" > eula.txt
RUN wget -O minecraft_server.jar https://launcher.mojang.com/v1/objects/84194a2f286ef7c14ed7ce0090dba59902951553/server.jar

ENTRYPOINT ["java", "-Xmx1024M", "-Xms1024M", "-jar", "minecraft_server.jar", "nogui"]
