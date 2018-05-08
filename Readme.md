This image is designed to be used as part of the [www.pool.ntp.org](https://ntppool.org) project.
Default is for the Australian zone

```sh
# Build
docker build -t publicarray/chrony .
# Run
docker run -it --rm --name chrony -p123:123/udp --cap-add SYS_TIME publicarray/chrony
# Run detached
docker run -d --rm --name chrony -p123:123/udp --cap-add SYS_TIME publicarray/chrony
# Using the host's rtc (realtime clock) [untested]
docker run -it --rm --name chrony -p123:123/udp --cap-add SYS_TIME -v /dev/rtc:/dev/rtc:ro publicarray/chrony
# BYO (bring your own) config file
docker run -it --rm --name chrony -p123:123/udp --cap-add SYS_TIME -v "$(pwd)"/chrony.conf:/etc/chrony.conf:ro publicarray/chrony
# Or your own arguments
docker run -it --rm --name chrony -p123:123/udp publicarray/chrony --help
```

```sh
# https://docs.docker.com/compose/compose-file/#cap_add-cap_drop
# this will not work :'( > Note: These options are ignored when deploying a stack in swarm mode with a (version 3) Compose file.
# https://github.com/docker/swarmkit/pull/1565
# docker stack deploy --compose-file=docker-compose.yml ntp-server
```
