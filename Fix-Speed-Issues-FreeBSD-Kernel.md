# fixing speed issues when hw checksum slow down the server
# add the following to /etc/sysctl.conf
net.inet.tcp.cc.algorithm=htcp

# after, you must recompile the kernel
need a kernel option too

# inside "/usr/src/sys/`uname -m`/conf/GENERIC", add the following:
GENERIC
options         TCPHPTS

# next, recompile the kernel
make buildkernel KERNCONF=GENERIC
make installkernel KERNCONF=GENERIC
make buildworld
make kernel KERNCONF=GENERIC
shutdown -r NOW
mergemaster -p
make installworld
shutdown -r NOW
mergemaster -i
make delete-old

