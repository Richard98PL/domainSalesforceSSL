# domainSalesforceSSL

1. get server.crt file with 
```
-----END CERTIFICATE-----
```
at the end


openssl x509 -outform der -in server.crt -out public_key.der
openssl x509 -in server.crt -pubkey > public_key.pem

keytool -importcert -file server.crt -keystore keystore.jks -alias mycertificate -storetype jks

openssl pkcs12 -inkey server.key -in server.crt -export -out keystore.p12 -name mykey

keytool -importkeystore -destkeystore keystore.jks -srckeystore keystore.p12 -srcstoretype pkcs12 -destalias mykey -srcalias mykey
