# Use the official OpenJDK 17 image as base
FROM openjdk:19-jdk-alpine

# Define the working directory
WORKDIR /spigot-server

# Download BuildTools.jar to build spigot server
ADD https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar /temp/

# Install git & build spigot server
RUN apk add --no-cache git \
    && java -jar /temp/BuildTools.jar --rev latest \
    && mv ./spigot-*.jar spigot.jar \


# Expose the necessary port
EXPOSE 25566

# Copy over server properties
COPY ./server.properties /spigot-server/
COPY ./whitelist.json /spigot-server/
COPY ops.json /spigot-server/

# Copy map folders
COPY ./.map/world /spigot-server/world
COPY ./.map/world_nether /spigot-server/world_nether
COPY ./.map/world_the_end /spigot-server/world_the_end

# Accept Minecraft EULA
RUN echo "eula=true" > eula.txt

RUN apk add screen

# Start the Spigot server
ENTRYPOINT screen -S MinecraftServer -dm java -Xmx1024M -Xms512M -jar /tmp/spigot-1.20.1.jar nogui