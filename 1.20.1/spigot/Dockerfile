# Use the official OpenJDK 17 image as base
FROM openjdk:17-jdk-alpine

# Define the working directory
WORKDIR /spigot-server

# Expose the necessary port 
EXPOSE 25566

# Copy over server properties and world data
COPY ./server.properties /spigot-server/
COPY ./whitelist.json /spigot-server/
COPY ./.map/ /spigot-server/

# Copy EULA 
COPY ./eula.txt /spigot-server/

# Accept Minecraft EULA
RUN echo "eula=true" > eula.txt

# Download BuildTools.jar to build spigot server
ADD https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar /temp/

# Install git & build spigot server
RUN apk add --no-cache git \
    && java -jar /temp/BuildTools.jar --rev latest \
    && mv spigot-*.jar spigot.jar \
    && rm -rf /temp

# Start the Spigot server
ENTRYPOINT ["java", "-Xmx1024M", "-Xms1024M", "-jar", "spigot.jar", "nogui"]