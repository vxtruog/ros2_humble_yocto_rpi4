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

git clone --depth=1 -b build https://github.com/ros/meta-ros
kas build meta-ros/kas/oeros-scarthgap-humble-raspberrypi4-64.yml

# lúc này có layer nào mà kas không build trực tiếp được thì git clone thủ công với --depth=, sao cho phù hợp với nhánh và commit mong muốn trong tệp .yml
# để check commit dùng git rev-parse HEAD
# nếu độ sâu depth chưa đủ để có nhánh commit phù hợp thì tăng thêm độ sâu dùng git fetch --depth=<độ_sâu_mong_muốn> <branch> <version>, sau đó git checkout vào mã commit phù hợp.
# một điều chú ý là meta-ros (build) để dùng kas, còn meta-ros(scarthgap) mới có các tệp để thêm vào bblayers.conf nhé, ta phải git clone cả hai nhánh này.
```

```
kết quả có trong: ~/build/tmp-glibc/deploy/images/raspberrypi4-64/
bunzip2 -f ros-image-core-humble-raspberrypi4-64.rootfs.wic.bz2
sudo dd if=ros-image-core-humble-raspberrypi4-64.rootfs.wic \
         of=/dev/sdX bs=4M conv=fdatasync status=progress         //X phải hợp lý với thư mục thẻ SD, dùng lsblk để check
```
