# deb-vz7-vzkernel
How to build OpenVZ 7 debian vzkernel package

## In clean environment do:

- `apt-get update -qq && apt-get -y dist-upgrade`
- `apt-get install -y bc build-essential cpio flex kmod libelf-dev libncurses5-dev`
- `git clone --depth 1 --branch rh7-3.10.0-862.11.6.vz7.71.13  https://src.openvz.org/scm/ovz/vzkernel.git`
- `cd vzkernel`
- `make mrproper`
- `cp config.OpenVZ .config`
- `make -j$(nproc) deb-pkg`
