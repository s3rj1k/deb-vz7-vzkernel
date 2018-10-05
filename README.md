# deb-vz7-vzkernel
How to build OpenVZ 7 debian vzkernel package (in clean environment)

## Set package maintainer:
 - `DEBEMAIL="11349489+s3rj1k@users.noreply.github.com"`
 - `DEBFULLNAME="s3rj1k"`
 - `export DEBEMAIL DEBFULLNAME`

## Install build dependencies:
- `apt-get update -qq && apt-get -y dist-upgrade`
- `apt-get install -y bc build-essential cpio flex kmod libelf-dev libncurses5-dev`

## Clone tagged release:
- `git clone --depth 1 --branch rh7-3.10.0-862.11.6.vz7.71.13  https://src.openvz.org/scm/ovz/vzkernel.git`

## Prepare kernel:
- `cd vzkernel`
- `make mrproper`

## Set kernel config:
- `cp config.OpenVZ .config`

## Run make:
- `make -j$(nproc) deb-pkg`

## Fix libc6-dev dependency:
In file `/var/lib/dpkg/status` find `Package: libc6-dev` and manually fix `Depends` filed,
changing `linux-libc-dev` dependency to needed version
