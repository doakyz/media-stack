# media-stack
All-In-One docker compose stack for media servers

This docker compose stack is designed to be used with minor editing to the ``.env`` file


In my case I have a NAS mounted under /share with the following folder layout 

```
share/
├── downloads
└── media
    ├── movies
    ├── music
    └── shows
```


### Prerequsite
- docker compose installed
- **Optional** - [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html) for using GPU decode in Plex

## How to
1. Edit ``.env`` to reflect the desired settings 

```
PUID=1000
PGID=1000
TZ=Etc/UTC
CONFIG=$PWD
SHARE=/path/to/share
```

2. Run ``docker compose up``
* During this initial startup phase qBitorrent will generate a temptemporary admin password. This will be visible in the docker logs

#### Example output of the temporary password
``qbittorrent  | The WebUI administrator password was not set. A temporary password is provided for this session: IuKLZqq9B``


3. Navigate to http://IP:8080/ to access the qbittorrent webui and sign in with the temporary password. 
4. Set a new admin password.
5. Set a new download location
- Following the folder structure of ``/share`` the download location in qbittorrent should be set to ``/share/downloads``
6. The docker stack can now be stopped and started in detached mode ``docker compose up -d``

In the default ``.env`` configuration, all of application volumes will be created in the same location of the ``docker-compose.yml``

```
# ls
bazarr  docker-compose.yml  .env  jellyseerr  lidarr  plex  prowlarr  qbittorrent  radarr  sonarr  tautulli
```

### Application Configuration
Because we're using a docker network, connecting the arrs apps is greatly simplified.
We're able to create connections using the container name and the port as a valid http URL

#### Prowlarr connecting to Radarr

![prowlarr-radarr](https://github.com/user-attachments/assets/1c8d247a-1adc-4937-b97e-aee6f46926cb)

This applies to all containers that are connected on the ``media`` docker network



| Service | URL |
| :----: | :----: |
| sonarr     | http://sonarr:8989    |
| radarr     | http://radarr:7878    |
| bazarr     | http://bazarr:7878    |
| prowlarr     | http://sonarr:9696    |
| lidarr     | http://lidarr:8686    |
| jellyseerr     | http://jellyseerr:5055    |
| qbittorrent     | http://qbittorrent:8080    |
| tautulli     | http://tautulli:8181    |
