# how to add additional IP addresses inside running jails
### you must run this as sudo, or else it will fail
ensure you type all existing IP addresses the server already has when you run this command:

### IPv4
sudo jail -m ip4.addr = "192.168.17.1,192.168.80.3" jid=$JID
### IPv6 
sudo jail -m ip6.addr = "2607:17:3::ab,2607:17:3::bc2,2607:17:3::ba:d" jid=$JID


