
# DigiCert Client Certificate Manager

### Description:
A Windows Python app with DigiCert's API for ordering DigiCert's Premium, Authentication Plus and Signature Plus Client Certificates. The CSR and Key generation are handled automatically using PyOpenSSL with the goal of creating the pfx (PKCS12) format. Upon a successful order the following directory and files are generated. 

    /Order_number_ID_number/order_number.pfx
    /Order_number_ID_number/certs.zip
    /Order_number_ID_number/csr.pem
    /Order_number_ID_number/key.pem

### Prerequisites:

 - Some knowledge of DigiCert's CertCentral platform and client certificates
 - A DigiCert API key (Admin)
 - Organization submitted with DigiCert and OV validated
 - DigiCert account balance option configured 
 - DigiCert account "One-Step" approval option configured 

### How it Works..
On the **Options** tab use `Load` to enter and save your API key. 

On the **Orders** tab, complete the fields and submit the request. At this point there are two scenarios. 
>NOTE: A file called 'data' is created in the local directory and holds the key for future use.

1) **Domain Validated**: If the domain used for the email address is OV validated in the DigiCert account the process is quick. The request is auto approved, certificate downloaded and a pfx (PKCS12) is created. The private key, CSR and .zip of the certificates issued are also saved. 

2) **Domain Not Validated**: If the domain used for the email address has not been previously validated, a popup shows letting you know there is an approval email to complete. If you can approve the request, use the retry option and it will attempt to finish the creation of the pfx (PKCS12). If for some reason the approval cannot be completed at this time, the key and CSR still exist in the directory created but you would be responsible for combining the certificate using another method. 

### Pictures:
 ![enter image description here](https://i.ibb.co/NN11x5r/ccm-v2-c2jy-IZTJTs.jpg)  ![enter image description here](https://i.ibb.co/HzjhmGT/ccm-v2-LOAEp1r-Pj-I.jpg)  ![enter image description here](https://i.ibb.co/vd872Xn/ccm-v2-s-Q7ub-Al-Ax-M.jpg) 

### Other Stuff:

DigiCert API docs can be found here [https://dev.digicert.com/](https://dev.digicert.com/)

Key generation/pfx creation is handled by PyOpenSSL ([https://www.pyopenssl.org/en/stable/](https://www.pyopenssl.org/en/stable/)) using the Python Cryptographic Module ([https://cryptography.io/en/latest/](https://cryptography.io/en/latest/)). 

The UI Theme is called Qtmodern and is awesome. Check it out here. [https://github.com/gmarull/qtmodern](https://github.com/gmarull/qtmodern)

Lastly, there most likely will be a crash somewhere as I continue to work on the project. Just remember if an order was placed and is not needed, cancel it in your DigiCert account within the first 30 days for a full refund. If anything else screws up in the actual ordering process, same applies.
#### Disclaimer:
Be smart and safe with the management of your certificates and keys. I am not liable and take no responsibility for any usage of this application and it's key generation. It comes with no warranty or guarantee whatsoever and most likely no support ;)

### Download: 
Windows App: https://drive.google.com/open?id=1KTZuXVRAerK4wQUuXMy5msRtD3oJyUab

Developed by: Ben Morse (morsewb@gmail.com)
April 2020



# Other Projects


## CertCentral Dashboard (WIP)
Prior to the client certificate app above this was my main project. It's a full UI for order management. I was pretty close to being done but wasn't really happy with how threading was handled. The app could hang with weird behavior. I started to see the effects of how Python handles memory allocation as well. The concept is based off of tab creation for each order you need to manage, which is cool but Python doesn't release the memory used to create the tabs when they are closed. 

Error handling or at least good error handling is tough to get right. There is basically none and the task seems huge. This spawned the client app project above so I could implement it as I go and on a smaller scale. 

![enter image description here](https://i.ibb.co/5xX23Xv/dash.jpg)

![enter image description here](https://i.ibb.co/J503bhd/dash2.jpg)

## Command Line Utility
In my adventures in Python and DigiCert's API I finally attempted to make a usable class from all of my previous scripts. This command line utility is one of the side projects that was spawned from it.

There's little error handling but it has some cool features like revoking by order ID or cert ID. You could also add notes per certificate. Once I had a grip on creating a UI with PyQT5 this work led to the app shown above. 

![enter image description here](https://i.ibb.co/zrLjk5q/cmd-line.jpg)

   
#### Download:
Windows Command Line Executable: https://drive.google.com/open?id=19y9vGFbShyxb3ePz4218aFdPHGmUEyX-

#### Disclaimer:

The Software Is Provided “as Is”, Without Warranty Of Any Kind, Express Or Implied, Including But Not Limited To The Warranties Of Merchantability, Fitness For A Particular Purpose, Title And Non-infringement. In No Event Shall The Copyright Holders Or Anyone Distributing The Software Be Liable For Any Damages Or Other Liability, Whether In Contract, Tort Or Otherwise, Arising From, Out Of Or In Connection With The Software Or The Use Or Other Dealings In The Software.


Developed by: Ben Morse ([morsewb@gmail.com](mailto:morsewb@gmail.com))

