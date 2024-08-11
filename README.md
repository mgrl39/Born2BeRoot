# Born2BeRoot Debian Tutorial

1. Descargar la maquina virtual

- Crear la maquina virtual en VirtualBox

![Imagen 151](steps/b2br_img_151.png)
![Imagen 152](steps/b2br_img_152.png)
![Imagen 153](steps/b2br_img_153.png)
![Imagen 154](steps/b2br_img_154.png)
![Imagen 155](steps/b2br_img_155.png)
![Imagen 156](steps/b2br_img_156.png)
![Imagen 157](steps/b2br_img_157.png)
![Imagen 158](steps/b2br_img_158.png)
![Imagen 159](steps/b2br_img_159.png)
![Imagen 160](steps/b2br_img_160.png)
![Imagen 161](steps/b2br_img_161.png)
![Imagen 162](steps/b2br_img_162.png)
![Imagen 163](steps/b2br_img_163.png)
![Imagen 164](steps/b2br_img_164.png)
![Imagen 165](steps/b2br_img_165.png)
![Imagen 166](steps/b2br_img_166.png)
![Imagen 167](steps/b2br_img_167.png)
![Imagen 168](steps/b2br_img_168.png)
![Imagen 169](steps/b2br_img_169.png)
![Imagen 170](steps/b2br_img_170.png)
![Imagen 171](steps/b2br_img_171.png)
![Imagen 172](steps/b2br_img_172.png)
![Imagen 173](steps/b2br_img_173.png)
![Imagen 174](steps/b2br_img_174.png)
![Imagen 175](steps/b2br_img_175.png)
![Imagen 176](steps/b2br_img_176.png)
![Imagen 177](steps/b2br_img_177.png)
![Imagen 178](steps/b2br_img_178.png)
![Imagen 179](steps/b2br_img_179.png)
![Imagen 180](steps/b2br_img_180.png)
![Imagen 181](steps/b2br_img_181.png)
![Imagen 182](steps/b2br_img_182.png)
![Imagen 183](steps/b2br_img_183.png)
![Imagen 184](steps/b2br_img_184.png)
![Imagen 185](steps/b2br_img_185.png)
![Imagen 186](steps/b2br_img_186.png)
![Imagen 187](steps/b2br_img_187.png)
![Imagen 188](steps/b2br_img_188.png)

### Script
```bash
#!/bin/bash

# Architecture
arch=$(uname -a)

# CPU Info
cpuf=$(lscpu | awk '/Socket\(s\):/ {print $2}')
cpuv=$(lscpu | awk '/^CPU\(s\):/ {print $2}')

# RAM Info
ram_total=$(free -m | awk '/Mem:/ {print $2}')
ram_use=$(free -m | awk '/Mem:/ {print $3}')
ram_percent=$(free -m | awk '/Mem:/ {printf("%.2f"), $3/$2*100}')

# Disk Info
disk_total=$(df -h --total | awk '/^total/ {print $2}')
disk_use=$(df -h --total | awk '/^total/ {print $3}')
disk_percent=$(df -h --total | awk '/^total/ {print $5}')

# CPU Load
cpu1=$(vmstat 1 2 | tail -1 | awk '{printf $15}')
cpu_op=$(expr 100 - $cpu1)
cpu_fin=$(printf "%.1f" $cpu_op)

# Last Boot
last_boot=$(who -b | awk '{print $3, $4}')

# LVM Usage
lvmu=$(lsblk | grep -q "lvm" && echo "yes" || echo "no")

# TCP Connections
tcp_conn=$(ss -tan | grep -c ESTAB)

# Logged Users
user_log=$(who | wc -l)

# Network Info
ip=$(hostname -I)
mac=$(ip link show | awk '/link\/ether/ {print $2}')

# Sudo Commands
sudo_cmd=$(journalctl _COMM=sudo | grep COMMAND | wc -l)

wall "	Architecture: $arch
	CPU physical: $cpuf
	vCPU: $cpuv
	Memory Usage: $ram_use/${ram_total}MB ($ram_percent%)
	Disk Usage: $disk_use/$disk_total ($disk_percent)
	CPU load: $cpu_fin%
	Last boot: $last_boot
	LVM use: $lvmu
	Connections TCP: $tcp_conn ESTABLISHED
	User log: $user_log
	Network: IP $ip ($mac)
	Sudo: $sudo_cmd cmd"
```
