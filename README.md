# Media Setup
This is a complete set of services to download and play video content.

## Services
* [Plex](https://www.plex.tv) is a media player that organizes and plays all of your local  media over the internet.
* [Sonarr](https://sonarr.tv) is a service that searches for and downloads episodes for tv shows and organizes them on your local machine
* [Radarr](https://radarr.video) is a service that searches for and downloads movies and organizes them on your local machine
* [Sabnzbd](https://sabnzbd.org) is a [Usenet](https://en.wikipedia.org/wiki/Usenet) downloader
* [rTorrent](https://github.com/binhex/arch-rtorrentvpn) is a torrent download client with vpn support

## Environmental Variables
This docker-compose file uses environmental variables in order for it to work:
|Env Var        |Description    |Example|
|:------------- |:-------------|:-----|
|${MEDIA_SERVER}|The IP address of the NFS server that holds your media|10.0.1.1
|${VIDEOS_DIR}|The path to the directory on the NFS server that holds all of your media|/path/to/videos
|${DOWNLOADS_DIR}|The path to the directory on the NFS server that holds all of your downloads|/path/to/downloads
|${TIMEZONE}|The [timezone](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) that you're in|America/New_York
|${PLEX_CLAIM}|In order to get this to work properly you'll need to get a claim token from [here](https://plex.tv/claim)|
|${SERVICES_CONFIG_DIR}|The path to the directory on your local machine which holds the config files for all of the services|/path/to/services/config
|${VPN_USERNAME}|The vpn username that rtorrent is going to use|username
|${VPN_PASSWORD}|The vpn password that rtorrent is going to use|password

### Setting up the Environmental Variables
In order to setup these environmentals you can run the commands below once to make it so that you don't have to se them up again. N.B. This is assuming that you're using a bash shell

```bash
echo "export MEDIA_SERVER=0.0.1.1" >> ~/.bash_profile
echo "export VIDEOS_DIR=/path/to/videos" >> ~/.bash_profile
echo "export DOWNLOADS_DIR=/path/to/downloads" >> ~/.bash_profile
echo "export TIMEZONE=America/New_York" >> ~/.bash_profile
echo "export PLEX_CLAIM=1234567890" >> ~/.bash_profile
echo "export SERVICES_CONFIG_DIR=/path/to/services/config" >> ~/.bash_profile
echo "export VPN_USERNAME=username" >> ~/.bash_profile
echo "export VPN_PASSWORD=password" >> ~/.bash_profile
source ~/.bash_profile
```

## Running the Services
if you don't need sudo in order to run docker-compose then:
```bash
docker-compose up -d
```

If you're running on ubuntu (an os that needs sudo to use docker-compose):
```bash
sudo -E docker-compose up -d
```
