# Home-Server-Plex-Setup (Docker)

This repository documents my home server setup for running Plex using Docker. It covers conatiner configuration, storage layout, local networking, and common troubleshooting steps.

The goal of this project is to demonstrate practical system administration skills, containerisation knoweledge, and real-world home lab experiance.

## Project Structure

* Docker
* Network
* Storage
* Troubleshooting

## Features

* Plex running in Docker
* Organised media storage layout
* Local network access
* Container updates and maintenance
* Troubleshooting notes
* Future improvements planned (static IP, remote access)

## Docker Compose

Below is the Docker Compose configuration used for Plex.

* Version: 3.9
* Image: linuxserver/plex
* Container name: Plex
* PUID: 1000
* PGID: 1000
* TZ: Europe/London
* Restart: Off

## Local Network Setup

Plex is currently running on the local network only. Future plans include setting this up for remote access which will need me to set up a static IP and port forwarding.

## Media Organisation

The folder structure and formats are set up in a particular way to better assist Plex pulling in metadata from external sources such as The Movie Database. If this is done incorrectly or if the format doesnt apply to way it is expected, you will get errors such as media not showing or will show as somethig else entirely.

Media
* /Movies
* /TV Shows

Each file has to match the database it pulls the information from. An example would be the file name might match another movie with the same name, which would pull in completly different data.

## Docker Notes

The UGREEN NAS hardware does not provide a built in Plex Media Server package, so Docker is used to run Plex independently of the NAS's limited software enviroment. While Synology is the most popular for home Plex Servers, UGREEN offers better hardware for the price. 

This includes more RAM and CPU power which is especially useful when more than person is accessing the server at the same time.

## Troubleshooting

I have had a number of seperate issues along the way which I have managed to resolve. 

This includes the following examples:

UGREEN NAS not having the abilty to natively run Plex Media Server. I was able to do some research and the best solution appeared to be installing Docker and allowing it to run a container for the Linux version of Plex.

Metadata not pulling through correctly. This is normally where the file name saved either doesnt match the database its pulling from, or where there is more than one film with the same name. This can be resolved by checking the database it pulls the infomation from, or by adding the year of release.

Server not avaliable. This has normally been the case where the NAS loses power such as temporary power loss. I do not have the auto restart feature on Docker, which helps inform me there was an issue. It gives me a heads up there was an unexpected shut down and I have to run the container again. This also highlights there could be a potential issue with data loss or corruption, meaning I should also check to make sure media appears fine.

## Future Enhancements

I want to set this up to be accessed externally in the future which will require me to set up a static IP and port forwarding on the network side of things. I would also need to get Plex premium to allow the software the correct permissions to do this.

I would also like to set up redundancy, but as I currently only have a 2 bay NAS, I would likely choose to have a external drive as a copy rather than setting up a raid configuration.

I have also been looking at using the NAS to host a small game server. This is something my devices hardware is capable off providing I limit resources. This would also require a static IP and port forwarding to help people from outside my LAN to be able to access. I would also need to do more research on the security side of this, which is why I havent set up the server to be accessed externally as of yet.
