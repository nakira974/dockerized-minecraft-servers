# compose-minecraft-servers
A docker-compose running multiple Minecraft Servers loading a specific map each.

You only have to create a folder called '.map' or else in your version folder, where there'll be inside the Minecraft World's folders, respectivly : 

- 'world',
- 'world_nether'
- world_the_end'

If these folders aren't created, servers' Dockerfile won't build, so make sure at least you created empty 3 empty folders, this due to the fact that a volume is mounted to share files between container and host, so that you can retreive your files at this place.
