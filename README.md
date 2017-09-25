#!/bin/bash
# Created by Kang wahid
if [[ -e /etc/debian_version ]]; then
	OS=debian
	RCLOCAL='/etc/rc.local'
elif [[ -e /etc/centos-release || -e /etc/redhat-release ]]; then
	OS=centos
	RCLOCAL='/etc/rc.d/rc.local'
	chmod +x /etc/rc.d/rc.local
else
	echo "Sepertinya Anda tidak menjalankan installer ini pada sistem Debian, Ubuntu atau CentOS"
	exit
fi
color1='\e[031;1m'
color2='\e[34;1m'
color3='\e[0m'
echo "--------------- Selamat Datang Di Vps Anda Boss ---------------"
	echo ""
	cname=$( awk -F: '/model name/ {name=$2} END {print name}' /proc/cpuinfo )
	cores=$( awk -F: '/model name/ {core++} END {print core}' /proc/cpuinfo )
	freq=$( awk -F: ' /cpu MHz/ {freq=$2} END {print freq}' /proc/cpuinfo )
	tram=$( free -m | awk 'NR==2 {print $2}' )
	swap=$( free -m | awk 'NR==4 {print $2}' )
	up=$(uptime|awk '{ $1=$2=$(NF-6)=$(NF-5)=$(NF-4)=$(NF-3)=$(NF-2)=$(NF-1)=$NF=""; print }')

	echo -e "\e[032;1mCPU model:\e[0m $cname"
	echo -e "\e[032;1mNumber of cores:\e[0m $cores"
	echo -e "\e[032;1mCPU frequency:\e[0m $freq MHz"
	echo -e "\e[032;1mTotal amount of ram:\e[0m $tram MB"
	echo -e "\e[032;1mTotal amount of swap:\e[0m $swap MB"
	echo -e "\e[032;1mSystem uptime:\e[0m $up"
	echo -e "------------------------------------------------------------------------------"
	echo -e "Seputar SSH & OpenVPN"
	echo -e "${color1}1${color3}. "${color1}Buat akun SSH & OpenVPN${color3})"
	echo -e "${color1}2${color3}. "${color1}Generate akun SSH/OpenVPN${color3})"
	echo -e "${color1}3${color3}. "${color1}Buat account trial untuk SSH & OpenVPN${color3})"
	echo -e "${color1}4${color3}. "${color1}Tambah masa aktif akun SSH & OpenVPN${color3})"
	echo -e "${color1}5${color3}. "${color1}Ganti password akun SSH/OpenVPN${color3})"
	echo -e "${color1}6${color3}. "${color1}Bannned user yang melakukan multilogin${color3})"
	echo -e "${color1}7${color3}. "${color1}Unbanned user SSH & OpenVPN yang terbanned${color3})"
	echo -e "${color1}8${color3}. "${color1}Mengunci user SSH & OpenVPN${color3})"
	echo -e "${color1}9${color3}. "${color1}Membuka user SSH & OpenVPN yang terkunci${color3})"
	echo -e "${color1}10${color3}. "${color1}Hapus Akun SSH & OpenVPN${color3})"
	echo -e "${color1}11${color3}. "${color1}Lihat detail user SSH & OpenVPN${color3})"
	echo -e "${color1}12${color3}. "${color1}Tampilkan daftar user SSH & OpenVPN${color3})"
	echo -e "${color1}13${color3}. "${color1}Cek login Dropbear, OpenSSH, dan OpenVPN${color3})"
	echo -e "${color1}14${color3}. "${color1}Lihat log login Dropbear & OpenSSH${color3})"
	echo -e "${color1}15${color3}. "${color1}Kill Multi Login${color3})"
	echo -e "${color1}16${color3}. "${color1}Tampilkan user yang akan expired dalam Terdekat${color3})"
	echo -e "${color1}17${color3}. "${color1}Tampilkan user yang telah expired${color3})"
	echo -e "${color1}18${color3}. "${color1}Hapus user SSH & OpenVPN yang telah expired${color3})"
	echo -e "${color1}19${color3}. "${color1}Kunci user SSH & OpenVPN yang telah expired${color3})"
	echo -e "${color1}20${color3}. "${color1}Lihat daftar user yang terkick${color3})"
	echo -e "${color1}21${color3}. "${color1}Lihat daftar user yang terbanned${color3})"
	echo -e "${color1}22${color3}. "${color1}Buat akun PPTP VPN${color3})"
	echo -e "${color1}23${color3}. "${color1}Hapus akun PPTP VPN${color3})"
	echo -e "${color1}24${color3}. "${color1}Lihat detail akun PPTP VPN${color3})"
	echo -e "${color1}25${color3}. "${color1}Cek login PPTP VPN (${color2}user-login-pptp${color3})"
	echo -e "${color1}26${color3}. "${color1}Lihat daftar user PPTP VPN (${color2}alluser-pptp${color3})"
	echo -e "${color1}27${color3}. "${color1}Speedtest server (${color2}speedtest --share${color3})"
	echo -e "${color1}28${color3}. "${color1}Benchmark server (${color2}bench-network${color3})"
	echo -e "${color1}29${color3}. "${color1}Lihat penggunaan RAM server (${color2}ram${color3})"
if [[ "$OS" = 'debian' ]]; then 
	echo -e "${color1}30${color3}. "${color1}Restart OpenSSH (${color2}service ssh restart${color3})"
	echo -e "${color1}31${color3}. "${color1}Restart Dropbear (${color2}service dropbear restart${color3})"
	echo -e "${color1}32${color3}. "${color1}Restart OpenVPN (${color2}service openvpn restart${color3})"
	echo -e "${color1}33${color3}. "${color1}Restart PPTP VPN (${color2}service pptpd restart${color3})"
	echo -e "${color1}34${color3}. "${color1}Restart Webmin (${color2}service webmin restart${color3})"
	echo -e "${color1}35${color3}. "${color1}Restart Squid Proxy (${color2}service squid3 restart${color3})"
else 
	echo -e "${color1}30${color3}. "${color1}Restart OpenSSH ${color3})"
	echo -e "${color1}31${color3}. "${color1}Restart Dropbear ${color3})"
	echo -e "${color1}32${color3}. "${color1}Restart OpenVPN ${color3})"
	echo -e "${color1}33${color3}. "${color1}Restart PPTP VPN ${color3})"
	echo -e "${color1}34${color3}. "${color1}Restart Webmin ${color3})"
	echo -e "${color1}35${color3}. "${color1}Restart Squid Proxy ${color3})"
fi
echo -e "${color1}36${color3}. "${color1}Edit Port Server ${color3})"
echo -e "${color1}37${color3}. "${color1}Set auto reboot pada server ${color3})"
echo -e "${color1}38${color3}. "${color1}Reboot server ${color3})"
echo -e "${color1}39${color3}. "${color1}Ganti Password Server${color3})"
echo -e "${color1}40${color3}. "${color1}Lihat log instalasi ${color3})"
echo -e "${color1}41${color3}. "${color1}Update now"
echo "-------------------------------------------"
read -p "Tulis Pilihan Anda (angka): " x
if test $x -eq 1; then
user-add
elif test $x -eq 2; then
user-generate
elif test $x -eq 3; then
trial
elif test $x -eq 4; then
user-aktif
elif test $x -eq 5; then
user-password
elif test $x -eq 6; then
read -p "Isikan Jumlah Maximal Login (1-2): " MULTILOGIN
user-ban $MULTILOGIN
elif test $x -eq 7; then
user-unban
elif test $x -eq 8; then
user-lock
elif test $x -eq 9; then
user-unlock
elif test $x -eq 10; then
user-delete
elif test $x -eq 11; then
user-detail
elif test $x -eq 12; then
user-list
elif test $x -eq 13; then
user-login
elif test $x -eq 14; then
user-log
elif test $x -eq 15; then
read -p "Isikan Jumlah Maximal Login (1-2): " MULTILOGIN
user-limit $MULTILOGIN
elif test $x -eq 16; then
infouser
elif test $x -eq 17; then
expireduser
elif test $x -eq 18; then
user-delete-expired
elif test $x -eq 19; then
clear
echo "Script ini berjalan secara otomatis setiap jam 12 malam"
echo "Anda tidak perlu menjalankannya secara manual"
echo "Jika anda tetap ingin menjalankan script ini, ketik user-expire"
elif test $x -eq 20; then
log-limit
elif test $x -eq 21; then
log-ban
elif test $x -eq 22; then
user-add-pptp
elif test $x -eq 23; then
user-delete-pptp
elif test $x -eq 24; then
user-detail-pptp
elif test $x -eq 25; then
user-login-pptp
elif test $x -eq 26; then
alluser-pptp
elif test $x -eq 27; then
speedtest --share
elif test $x -eq 28; then
bench-network
elif test $x -eq 29; then
ram
elif test $x -eq 30; then
	if [[ "$OS" = 'debian' ]]; then 
		service ssh restart 
	else 
		service sshd restart 
	fi
elif test $x -eq 31; then
service dropbear restart
elif test $x -eq 32; then
service openvpn restart
elif test $x -eq 33; then
	if [[ "$OS" = 'debian' ]]; then 
		service pptpd restart 
	else 
		service pptpd restart 
	fi
elif test $x -eq 34; then
service webmin restart
elif test $x -eq 35; then
	if [[ "$OS" = 'debian' ]]; then 
		service squid3 restart 
	else 
		service squid restart 
	fi
elif test $x -eq 36; then
edit-port
elif test $x -eq 37; then
auto-reboot
elif test $x -eq 38; then
reboot
elif test $x -eq 39; then
passwd
elif test $x -eq 40; then
log-install
elif test $x -eq 41; then
wget http://autoscriptnobita.tk/install-premiumscript.sh -O - -o /dev/null|sh
else
echo "Pilihan Tidak Terdapat Di Menu."
exit
fi
