## V2 Changes
Only some minor changes have taken place in the v2 stack.

The main changes are the additions of the QoL tools; Profilarr and Qui to the primary media stack.

Profilarr is used to easily manage and automate updates for quality profiles in Sonarr and Radarr. 
Within Profilarr, the [Dumpstarr](https://github.com/Dumpstarr/Dumpstarr) repo has been selected as it’s a good combo of Dictionarry and TRaSH.

Qui is lightweight qBittorrent front end that can support multiple clients as well as functioning on mobile.


The secondary compose file contains applications used to run the Emby media server and the IPTV support programs Dispatcharr and Enhanced Channel Manager


#### V2 Docker network mapping
| Service | URL |
| :----: | :----: |
| sonarr     | http://sonarr:8989    |
| radarr     | http://radarr:7878    |
| bazarr     | http://bazarr:6767    |
| prowlarr     | http://prowlarr:9696    |
| lidarr     | http://lidarr:8686    |
| jellyseerr     | http://jellyseerr:5055    |
| qbittorrent     | http://qbittorrent:8080    |
| tautulli     | http://tautulli:8181    |
| profilarr     | http://profilarr:6868   |
| qui     | http://qui:7476    |

#### IPTV Compose container mapping
| Service | URL |
| :----: | :----: |
| emby     | http://emby:8096    |
| dispatcharr     | http://dispatcharr:9191    |
| ecm     | http://ecm:6100    |
