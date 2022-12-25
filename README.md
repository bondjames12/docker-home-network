# Description
This is the updated docker compose repo of all the media and home server apps

### FRONTENDS
* Traefik - Reverse Proxy
* OAuth - Forward Authentication
* Portainer - Container Management
* Organizr - Unified Frontend
* Heimdall - Unified Frontend Alternative
* Autoindex - Plain text Index to All Files

### SMART HOME

* HA-Dockermon - Manage Docker containers in Home Assistant 
* Mosquitto - MQTT Broker
* ZoneMinder - Video Surveillance 

### DATABASE

* phpMyAdmin - Database management
* InfluxDB - Database for sensor data
* mariadb - Database
* Grafana - Graphical data visualization for InfluxDB data
* Varken - Monitor Plex, Sonarr, Radarr, and Other Data

### DOWNLOADERS

* jDownloader - Download management
* SABnzbd - Binary newsgrabber (NZB downloader)
* qBittorrent - Torrent downloader
* TransmissionBT - Torrent Downloader

### INDEXERS

* Jackett - Torrent proxy
* NZBHydra2 - NZB meta search

### PVRS

* Lidarr - Music Management
* Radarr - Movie management
* Sonarr - TV Shows management

### MEDIA SERVER

* Plex - Media Server
* Jellyfin - Media Server
* Emby - Media Server
* Tautulli - Previously PlexPy. Plex statistics and monitoring
* Plex-Sync - For Syncing watched status between plex servers 
* Telly Tv- IPTV proxy for Plex

### MEDIA FILE MANAGEMENT

* Bazarr - Subtitle Management
* Picard - Music Library Tagging and Management
* Handbrake - Video Conversion (Transcoding and compression)
* MKVToolNix - Video Editing (Remuxing - changing media container while keeping original source quality)
* MakeMKV - Video Editing (Ripping from Disks)
* FileBot - File renamer

### SYSTEM

* Firefox - Web Broswer
* Glances - System Information
* Logarr - Log Management
* Monitorr - Webfront to display the status of any webapp or service
* APCUPSD - APC UPS Management
* qDirStat - Directory Statistics
* Guacamole - Remote desktop, SSH, on Telnet on any HTML5 Browser 
* Guacamole Daemon - Needed for Guacamole
* StatPing - Status Page & Monitoring Server

### MAINTENANCE

* Ouroboros - Automatic Docker Container Updates
* Docker-GC - Automatic Docker Garbage Collection

# Usage

First, install Docker and Docker Compose, as described in our <a href="https://www.smarthomebeginner.com/docker-home-media-server-2018-basic/">Docker Media Server guide</a>. 

1. Clone the repo.
2. Configure `traefik.toml`
  * Rename `traefik\traefik.toml.example` to `traefik\traefik.toml`
  * Edit it to reflect your situation
  * Edit domain name. 
  * DNS Challenge (for LetsEncrypt verification) is enabled by default for cloudflare. Use the [Traefik Reverse Proxy guide](https://www.smarthomebeginner.com/traefik-reverse-proxy-tutorial-for-docker/) for help with this.
  * For other providers other than cloudflare, [check here](https://docs.traefik.io/v2.0/https/acme/#providers).
3. (Optional) Enable or use HTTP Basic Authentication by renaming `shared\.htpasswd.example` to `shared\.htpasswd` in the folder and adding username and hashed password to it. 
4. Configure environmental variables (`.env` file)
  * Rename the included `.env.example` to `.env`.
  * Edit variables in `.env` file. 
  * All variables (ie. `${XXX}`) in docker-compose.yml come from `.env` file stored in the same place as docker-compose.yml. 
  * Ensure good permissions for the `.env` file (recommended: 640).
5. Edit `docker-compose.yml` to include only the services you want or add additional services to it. Be sure to read the comments for each app and create any required files.
6. Start and stop your docker stack as described in our [Docker Media Server guide](https://www.smarthomebeginner.com/docker-home-media-server-2018-basic/).
7. (Optional) Put non-docker apps behind Traefik proxy by renaming `traefik\rules\app.toml.example` to `traefik\rules\app.toml` and editing its contents.
