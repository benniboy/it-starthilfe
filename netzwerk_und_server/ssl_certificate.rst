in zb n

/etc/nginx/sites/ssl
touch makeselfsigned.sh
cat makeselfsigned.sh 

und die 3 zeilen einfügen
#!/bin/sh

SSLDOMAIN=$1
openssl req -x509 -nodes -days 2000 -subj "/C=AT/ST=TIROL/L=Innsbruck/O=Klein und Partner KG/OU=Security/CN=$SSLDOMAIN" -newkey rsa:1024 -keyout $SSLDOMAIN.pem -out $SSLDOMAIN.pem

dann mit ./makeselfsigned.sh DOMAINNAME

und bei nginx dann in der zb sites-avaiable/seitenname des editiern/eignebn

server {
  listen 443 default_server ssl;
  ssl_certificate      /usr/local/nginx/conf/cert.pem;
  ssl_certificate_key  /usr/local/nginx/conf/cert.key;  
  ...
}




http to https redirect



server {
       listen         80;
       server_name    my.domain.com;
       rewrite        ^ https://$server_name$request_uri? permanent;
}

server {
       listen         443;
       server_name    my.domain.com;

       ssl            on;

       [....]
}
