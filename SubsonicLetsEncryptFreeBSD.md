# Have Subsonic use letsencrypt certs for SSL 
cd /usr/local/etc/letsencrypt/live/`uname -n`
## create trust chain
cat privkey.pem > subsonic.crt
cat cert.pem >> subsonic.crt
cat chain.pem >> subsonic.crt
## convert cert to pkcs12
openssl pkcs12 -in subsonic.crt -out subsonic.pkcs12
## import pkcs12 into the java keystore#
### use the password 'subsonic' for everything prompted
keytool -importkeystore -srckeystore subsonic.pkcs12 -destkeystore subsonic.keystore -srcstoragetype PKCS12 -srcalias 1 -destalias subsonic
## find the subsonic-booter file within the installation dir of your server
zip /var/subsonic/standalone/subsonic-booter-jar-with-dependencies.jar subsonic.keystore
## restart service
/usr/local/etc/rc.d/subsonic restart
