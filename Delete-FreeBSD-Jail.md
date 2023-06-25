
### to delete a jail in FreeBSD, the path is unable to be rm -rf'd until this command is ran
chflags -R noschg $jail

### afterwards, rm -rf $jail works 
