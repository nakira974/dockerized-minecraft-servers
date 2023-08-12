# Use the official OpenJDK 17 image as base
FROM openjdk:19-jdk-alpine

# Define the working directory
WORKDIR /spigot-server

# Expose the necessary port
EXPOSE 25567

# Download BuildTools.jar to build spigot server
ADD https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar /temp/

# Install git & build spigot server
RUN apk add --no-cache git \
    && java -jar /temp/BuildTools.jar --rev latest \


# Copy over server properties and world data
COPY ./server.properties /spigot-server/
COPY .properties/blacklist.json /spigot-server/
COPY .properties/ops.json /spigot-server/


COPY ./.map/world /spigot-server/world
COPY ./.map/world_nether /spigot-server/world_nether
COPY ./.map/world_the_end /spigot-server/world_the_end


# Copy EULA
COPY .properties/eula.txt /spigot-server/

# Accept Minecraft EULA
RUN echo "eula=true" > eula.txt

RUN cd /spigot-server

# Start the Spigot server
ENTRYPOINT ["java", "-Xmx1024M", "-Xms1024M", "-jar", "/tmp/spigot-1.20.1.jar", "nogui"]