# initd
run  .sh script at startup example:https://gist.github.com/drmalex07/298ab26c06ecf401f66c

# systemd https://man7.org/linux/man-pages/man1/systemd.1.html
toolbox with thing like run command with timer or socket activation

# sar
https://www.geeksforgeeks.org/sar-command-linux-monitor-system-performance/
logs under given time frame and show cpu stats
systemctl start sysstat.service
sar -u 2 5


# nmap check network ports and stuff
nmap 217.72.52.82 -Pn

# ansible
setups a fresh vps and install and run correct docker stuff
usefull if handling large amount of servers