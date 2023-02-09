# Minecraft Spigot Server

## Setting Up Minecraft Server
* Prereqs for BuildTools: https://www.spigotmc.org/wiki/buildtools/#linux
* For above Minecraft 1.17.1, OpenJDK 17 needs to be installed:
```
sudo yum install git java-17-openjdk-devel
```
* Download 
```
curl -o BuildTools.jar https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar
```
* Run the BuildTools.jar from the command line:
```
git config --global --unset core.autocrlf
java -jar BuildTools.jar
```

## Fedora firewall
```
sudo firewall-cmd --permanent --zone=public --add-port=25565/tcp
```
