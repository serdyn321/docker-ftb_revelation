# Feed-The-Beast Revelation (Modded Minecraft 1.12) in Docker
To pull the image:
```
docker pull audiohacked/ftb_revelation:stable
```

It's highly recommended run a named data volume:
```
docker volume create minecraft_ftb_revelation_data
docker volume create minecraft_ftb_revelation_backups
```

Then, run the server container:
```
docker run --detach --interactive --tty \
    --name ftb_revelation \
    --volume minecraft_ftb_revelation_data:/minecraft/world \
    --volume minecraft_ftb_revelation_backups:/minecraft/backups \
    --publish 25565:25565 \
    --env EULA=TRUE \
    audiohacked/ftb_revelation:stable
```

## Building the Container Locally
 * clone the repository
  * cd into the cloned directory and run
 ```
 sudo docker build -t <INSERT A NAME HERE> .
 ```
 this will build the container and fetch version 2.4.1 of revalations
 * run these commands to make the directories needed for the volumes
 ```
 sudo mkdir -p /minecraft/world
 sudo mkdir -p /minecraft/backups
 ```
 * assuming you created the docker volumes above, you can now run
 ```
docker run --detach --interactive --tty \
    --name ftb_revelation \
    --volume minecraft_ftb_revelation_data:/minecraft/world \
    --volume minecraft_ftb_revelation_backups:/minecraft/backups \
    --publish 25565:25565 \
    --env EULA=TRUE \
    <NAME YOU INSERTED IN THE BUILD STEP>
```