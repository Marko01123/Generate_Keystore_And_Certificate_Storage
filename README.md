# Generate_Keystore_And_Certificate_Storage
Java GUI application for generating keystore and certificate storage. The implementation includes creating a keystore where user 
can generate a new AES key and a pair of RSA keys, and display them in a TextArea. After that, user can export a certificate from the 
keystore, save it in DER format, and display the certificate. Certificate encoding in Base64 is also implemented. Furthermore, 
the user can generate a .csr file, certificate signing request. Bouncy castle .jar file is included in repository.

These are cmd lines that are implemented in this application:
1. Creating keystore and generating new pair of RSA keys and storing them into keystore

keytool -genkey -alias RSAPrivatniKljuc -keysize 2048 -v -keyalg RSA -keystore {path}/SkladisteKljuceva.keystore

2. Displaying the content of keystore

keytool -list -keystore {path}/SkladisteKljuceva.keystore

3. Exporting RSA certificate in DER format 

keytool -export -alias RSAsertifikat -keystore {path}/SkladisteKljuceva.keystore -file {path}sertifikat.der

4. Encoding RSA certificate in BASE64 format and displaying the content of keystore:

keytool -export -alias RSAsertifikat -keystore {path}/SkladisteKljuceva.keystore -rfc -file {path}sertifikat.b64

keytool -printcert -alias RSAsertifikat -v -file {path}sertifikat.b64

5. Creating a request for a digital signature - CSR (Certificate Signing Request) form.

keytool -certreq -v -alias parKljuceva -keystore {path}/SkladisteKljuceva.keystore -file {path}sertifikat.csr
