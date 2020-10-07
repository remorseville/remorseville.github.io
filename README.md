<h1 id="digicert-script-examples---october-2020">DigiCert Script Examples - October 2020</h1>
<p>Use case examples in Python with DigiCert’s API</p>
<ul>
<li><a href="https://github.com/remorseville/digicert_scripts">Automating User Access</a></li>
<li><a href="https://github.com/remorseville/digicert_mutli_year_script/blob/main/README.md">Multi Year Certificate Management / Export CSV</a></li>
<li><a href="https://github.com/remorseville/DigiCert_Auth-key">Auth_key and Instant Issuance</a></li>
</ul>
<h1 id="april-2020">April 2020</h1>
<p>Going a different route I’ve decided to see what was possible using Flask to build my app. (<a href="https://flask.palletsprojects.com/en/1.1.x/">https://flask.palletsprojects.com/en/1.1.x/</a>). I’d like the most modern looking UI possible and Flask ties in HTML, jQuery and JavaScript. The UI options basically open up to to anything web development has to offer. It’s a huge difference.</p>
<p>I’m not looking to create a website, but turn the project into a local running app similar to what Electron can provide. I have some of the basic back end proof of concept done and started to work on the UI as well. Here’s a pic!</p>
<p><img src="https://i.ibb.co/r0BDBT2/chrome-c-Lc-M05-T7-Wh.jpg" alt="https://i.ibb.co/r0BDBT2/chrome-c-Lc-M05-T7-Wh.jpg"></p>
<h1 id="digicert-client-certificate-manager---april-2020">DigiCert Client Certificate Manager - April 2020</h1>
<h3 id="description">Description:</h3>
<p>A Windows Python app with DigiCert’s API for ordering DigiCert’s Premium, Authentication Plus and Signature Plus Client Certificates. The CSR and Key generation are handled automatically using PyOpenSSL with the goal of creating the pfx (PKCS12) format. Upon a successful order the following directory and files are generated.</p>
<pre><code>/Order_number_ID_number/order_number.pfx
/Order_number_ID_number/certs.zip
/Order_number_ID_number/csr.pem
/Order_number_ID_number/key.pem
</code></pre>
<h3 id="prerequisites">Prerequisites:</h3>
<ul>
<li>Some knowledge of DigiCert’s CertCentral platform and client certificates</li>
<li>A DigiCert API key (Admin)</li>
<li>Organization submitted with DigiCert and OV validated</li>
<li>DigiCert account balance option configured</li>
<li>DigiCert account “One-Step” approval option configured</li>
</ul>
<h3 id="how-it-works..">How it Works…</h3>
<p>On the <strong>Options</strong> tab use <code>Load</code> to enter and save your API key.</p>
<p>On the <strong>Orders</strong> tab, complete the fields and submit the request. At this point there are two scenarios.</p>
<blockquote>
<p>NOTE: A file called ‘data’ is created in the local directory and holds the key for future use.</p>
</blockquote>
<ol>
<li>
<p><strong>Domain Validated</strong>: If the domain used for the email address is OV validated in the DigiCert account the process is quick. The request is auto approved, certificate downloaded and a pfx (PKCS12) is created. The private key, CSR and .zip of the certificates issued are also saved.</p>
</li>
<li>
<p><strong>Domain Not Validated</strong>: If the domain used for the email address has not been previously validated, a popup shows letting you know there is an approval email to complete. If you can approve the request, use the retry option and it will attempt to finish the creation of the pfx (PKCS12). If for some reason the approval cannot be completed at this time, the key and CSR still exist in the directory created but you would be responsible for combining the certificate using another method.</p>
</li>
</ol>
<h3 id="pictures">Pictures:</h3>
<p><img src="https://i.ibb.co/NN11x5r/ccm-v2-c2jy-IZTJTs.jpg" alt="enter image description here">  <img src="https://i.ibb.co/HzjhmGT/ccm-v2-LOAEp1r-Pj-I.jpg" alt="enter image description here">  <img src="https://i.ibb.co/vd872Xn/ccm-v2-s-Q7ub-Al-Ax-M.jpg" alt="enter image description here"></p>
<h3 id="other-stuff">Other Stuff:</h3>
<p>DigiCert API docs can be found here <a href="https://dev.digicert.com/">https://dev.digicert.com/</a></p>
<p>Key generation/pfx creation is handled by PyOpenSSL (<a href="https://www.pyopenssl.org/en/stable/">https://www.pyopenssl.org/en/stable/</a>) using the Python Cryptographic Module (<a href="https://cryptography.io/en/latest/">https://cryptography.io/en/latest/</a>).</p>
<p>The UI Theme is called Qtmodern and is awesome. Check it out here. <a href="https://github.com/gmarull/qtmodern">https://github.com/gmarull/qtmodern</a></p>
<p>Lastly, there most likely will be a crash somewhere as I continue to work on the project. Just remember if an order was placed and is not needed, cancel it in your DigiCert account within the first 30 days for a full refund. If anything else screws up in the actual ordering process, same applies.</p>
<h4 id="disclaimer">Disclaimer:</h4>
<p>Be smart and safe with the management of your certificates and keys. I am not liable and take no responsibility for any usage of this application and it’s key generation. It comes with no warranty or guarantee whatsoever and most likely no support ;)</p>
<h3 id="download">Download:</h3>
<p>Windows App: <a href="https://drive.google.com/open?id=1KTZuXVRAerK4wQUuXMy5msRtD3oJyUab">https://drive.google.com/open?id=1KTZuXVRAerK4wQUuXMy5msRtD3oJyUab</a></p>
<p>Developed by: Ben Morse (<a href="mailto:morsewb@gmail.com">morsewb@gmail.com</a>)<br>
April 2020</p>
<h1 id="other-projects">Other Projects</h1>
<h2 id="certcentral-dashboard-wip">CertCentral Dashboard (WIP)</h2>
<p>Prior to the client certificate app above this was my main project. It’s a full UI for order management. I was pretty close to being done but wasn’t really happy with how threading was handled. The app could hang with weird behavior. I started to see the effects of how Python handles memory allocation as well. The concept is based off of tab creation for each order you need to manage, which is cool but Python doesn’t release the memory used to create the tabs when they are closed.</p>
<p>Error handling or at least good error handling is tough to get right. There is basically none and the task seems huge. This spawned the client app project above so I could implement it as I go and on a smaller scale.</p>
<p><img src="https://i.ibb.co/5xX23Xv/dash.jpg" alt="enter image description here"></p>
<p><img src="https://i.ibb.co/J503bhd/dash2.jpg" alt="enter image description here"></p>
<h2 id="command-line-utility">Command Line Utility</h2>
<p>In my adventures in Python and DigiCert’s API I finally attempted to make a usable class from all of my previous scripts. This command line utility is one of the side projects that was spawned from it.</p>
<p>There’s little error handling but it has some cool features like revoking by order ID or cert ID. You could also add notes per certificate. Once I had a grip on creating a UI with PyQT5 this work led to the app shown above.</p>
<p><img src="https://i.ibb.co/zrLjk5q/cmd-line.jpg" alt="enter image description here"></p>
<h4 id="download-1">Download:</h4>
<p>Windows Command Line Executable: <a href="https://drive.google.com/open?id=19y9vGFbShyxb3ePz4218aFdPHGmUEyX-">https://drive.google.com/open?id=19y9vGFbShyxb3ePz4218aFdPHGmUEyX-</a></p>
<h4 id="disclaimer-1">Disclaimer:</h4>
<p>The Software Is Provided “as Is”, Without Warranty Of Any Kind, Express Or Implied, Including But Not Limited To The Warranties Of Merchantability, Fitness For A Particular Purpose, Title And Non-infringement. In No Event Shall The Copyright Holders Or Anyone Distributing The Software Be Liable For Any Damages Or Other Liability, Whether In Contract, Tort Or Otherwise, Arising From, Out Of Or In Connection With The Software Or The Use Or Other Dealings In The Software.</p>
<p>Developed by: Ben Morse (<a href="mailto:morsewb@gmail.com">morsewb@gmail.com</a>)</p>

