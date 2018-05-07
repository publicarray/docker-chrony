This image is designed to be used as part of the [www.pool.ntp.org](https://ntppool.org) project.
Default is for the Australian zone

```sh
# Build
docker build -t publicarray/chrony .
# Run
docker run -it --rm --name chrony --cap-add SYS_TIME publicarray/chrony
# Using the host's rtc (realtime clock) [untested]
docker run -it --rm --name chrony --cap-add SYS_TIME -v /dev/rtc:/dev/rtc:ro publicarray/chrony
# BYO (bring your own) config file
docker run -it --rm --name chrony --cap-add SYS_TIME -v "$(pwd)"/chrony.conf:/etc/chrony.conf:ro publicarray/chrony
# Or your own arguments
docker run -it --rm --name chrony publicarray/chrony --help
```
