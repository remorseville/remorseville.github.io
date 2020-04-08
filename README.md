---


---

<h2 id="digicert-client-certificate-manager">DigiCert Client Certificate Manager</h2>
<h3 id="description">Description:</h3>
<p>A Python app with DigiCert’s API for ordering DigiCert’s Premium, Authentication Plus and Signature Plus Client Certificates. The CSR and Key generation are handled automatically using PyOpenSSL with the goal of creating the pfx (PKCS12) format. Upon a successful order the following directory and files are generated.</p>
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
<p>Developed by: Ben Morse (<a href="mailto:morsewb@gmail.com">morsewb@gmail.com</a>)<br>
April 2020</p>

