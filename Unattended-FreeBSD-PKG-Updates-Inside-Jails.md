#!/usr/local/bin/bash
pkg update -f && pkg upgrade -y
for n in `jls|cut -c4-6|sed 's/JID//g'|sed 's/^\ //g'|tail -n +2`; 
  do
    jexec $n pkg update -f
    jexec $n pkg upgrade -y
  done