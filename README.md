# TLS client athentication in nginx with PHP

This is a demo project to showcase TLS client authentication in nginx with PHP
to then process the data of the user.

## Docker Compose

This project is intended to be run using docker compose. Run `docker-compose up -d`
to start the web server. Access it via https://localhost/index.php

## Client Certificates

All certificates have been created using OpenXPKI, but any other source of X509
ertificates will work as well. To create your own client certificate:

1 Go to https://demo.openxpki.org/openxpki/
1 Login as "User" and choose any username as well as password
1 Request a "TLS Client" certificate. Logout.
1 Login as "Operator" with username "raop" and password "openxpki"
1 Approve the certificate request from your user. Logout.
1 Login as the previous user again; download the certificate + keys
1 Install that client certificate in your web browser

## Server Certificate

This repository comes with a preset server certificate that was created similar
to the above client certificate - of course by choosing "TLS Web Server" instead
of "TLS Client" as type.

To create your own certificate, you can again use the OpenXPKI. To use a server
certificate created there under nginx, you will have to convert the format from
PKCS12 to PEM. This can be achieved by the following command:

`openssl pkcs12 -in certificate.p12 -out certificate.crt -nodes`
