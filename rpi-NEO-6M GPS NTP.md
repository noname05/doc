1. 업데이트 
sudo apt-get update

sudo apt-get upgrade

2. cmdline.txt, config.txt 수정
sudo nano -w /boot/cmdline.txt

cmdline.txt에서 console=ttyAMA0,115200,kgdboc=ttyAMA0,115200 부분을 삭제하고

"dwc_otg.lpm_enable=0 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline rootwait"만 남겨 놓는다.

sudo nano -w /boot/config.txt

config.txt에 아래 내용을 추가

core_freq=250
enable_uart=1
dtoverlay=pi3-mini uart-bt

3. tty service 중지
sudo systemctl stop serial-getty@ttyS0.service
sudo systemctl disable serial-getty@ttyS0.service

4. reboot

5. 시리얼 통신 설정
stty -F /dev/ttyAMA0 raw 9600 cs8 clocal -cstopb

6. GPS 테스트
cat /dev/ttyS0


