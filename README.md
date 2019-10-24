# Docker-7DaysToDie
7 days to die LATEST EXPERIMENTAL server using LinuixGSM script in Docker

## IMPORTANT

Rigth now this image its working well, i have been using for a week without any problem

## USAGE

### START MODES:

#### 0 = Install server

#### 1 = Start server

#### 2 = Update server TO STABLE

#### 3 = Update server TO STABLE and start

#### 4 = Update server TO LATEST_EXPERIMENTAL

#### 5 = Update server TO LATEST_EXPERIMENTAL and start

### Docker

### FIRST Start, to install server
```bash
$ mkdir -p /path/to/7DaysToDie && mkdir -p /path/to/ServerFiles && sudo chown -R 1001:1001 /path/to/7DaysToDie && sudo chown -R 1001:1001 /path/to/ServerFiles
$ docker run --name 7dtdserver --restart unless-stopped -it -v "/path/to/7DaysToDie:/home/sdtdserver/.local/share/7DaysToDie/" -v "/path/to/ServerFiles:/home/sdtdserver/serverfiles/" -p 26900:26900/tcp -p 26900:26900/udp -p 26901:26901/udp -p 26902:26902/udp -p 8081:8081/tcp -p 8082:8082/tcp vinanrra/7dtd
```
### SECOND start to start/update server
```bash
$ docker run --name 7dtdserver --restart unless-stopped -it -v "/path/to/7DaysToDie:/home/sdtdserver/.local/share/7DaysToDie/" -v "/path/to/ServerFiles:/home/sdtdserver/serverfiles/" -p 26900:26900/tcp -p 26900:26900/udp -p 26901:26901/udp -p 26902:26902/udp -p 8081:8081/tcp -p 8082:8082/tcp -e START_MODE=CHANGE_ME vinanrra/7dtd
```

Ports 8081 and 8082 are OPTIONAL

### docker-compose

```bash
$ mkdir -p /path/to/7DaysToDie && mkdir -p /path/to/ServerFiles && sudo chown -R 1001:1001 /path/to/7DaysToDie && sudo chown -R 1001:1001 /path/to/ServerFiles
```

```
version: '2'
services:
  7dtd:
    image: vinanrra/7daystodie_latestexperimental
    container_name: 7dtd
    environment:
      - START_MODE=0 #Change between START MODES
    volumes:
    - ./ServerFiles:/home/sdtdserver/serverfiles/ #Optional if you dont care about serverfiles
    - ./7DaysToDie:/home/sdtdserver/.local/share/7DaysToDie/ #Optional if you dont care about maps files
    ports:
    - 26900:26900/tcp
    - 26900:26900/udp
    - 26901:26901/udp
    - 26902:26902/udp
    - 8081:8081/tcp #OPTIONAL WEBUI
    - 8082:8082/tcp #OPTIONAL WEBSERVER https://7dtd.illy.bz/wiki/Server%20fixes
    restart: unless-stopped
```
