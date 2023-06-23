#!/usr/local/bin/bash
freebsd-update fetch && freebsd-update install
echo "isengard updated"
for n in `jls|cut -c4-6|sed 's/JID//g'|sed 's/^\ //g'|tail -n +2`; 
  do
    jexec $n freebsd-update fetch && jexec $n freebsd-update install
  done
