# ros2_humble_yocto_rpi4
```
su -
usermod -aG sudo <user>
exit
reboot

sudo apt update
sudo apt upgrade

sudo apt install gawk wget git-core diffstat unzip texinfo gcc build-essential \
chrpath socat cpio python3 python3-pip python3-pexpect xz-utils debianutils \
iputils-ping python3-git python3-jinja2 python3-subunit zstd liblz4-tool file \
locales libacl1 libsdl1.2-dev xterm python3-venv lz4 gfortran

sudo locale-gen en_US.UTF-8
sudo update-locale LANG=en_US.UTF-8
echo 0 | sudo tee /proc/sys/kernel/apparmor_restrict_unprivileged_userns
```

```
python3 -m venv venv
source venv/bin/activate
pip3 install kas

git clone -b build https://github.com/ros/meta-ros
```
