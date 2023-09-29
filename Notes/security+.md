## Network device
<ul>
<li>Hubs</li>
<li>Switches(L2/L3)</li>
<li>Routers</li>
<li>Firewalls</li>

</ul>


## Proxies and different types of them
we have two kind of proxies:<code>Forward Proxy</code>,<code>Reverse Proxy</code>



## WAF(web app firewall) vs Next-Gen Firewall
Think of an NGFW as the entrance to a hotel and the WAF as the key to a hotel room. Network firewalls cover the traffic on the network; WAFs cover the app.<a href="https://www.f5.com/c/landing/waf-vs-ngfw-which-technology-do-you-need">Source</a>
WAF works in reverse proxy mode,and most important thing it does is checking input value.

## TCP/IP Model
for more inforamation please visit  this <a href="https://www.tcpipguide.com">Source</a>

## What is TTL?
Time-to-live (TTL) is a value for the period of time that a packet, or data, should exist on a computer or network before being discarded. The meaning of TTL, or packet lifetime, depends on the context
<a href="https://www.techtarget.com/searchnetworking/definition/time-to-live">Source</a>

## Is ICMP UDP?
Unlike the Internet Protocol (IP), ICMP is not associated with a transport layer protocol such as TCP or UDP. This makes ICMP a connectionless protocol: one device does not need to open a connection with another device before sending an ICMP message
<a href="https://www.cloudflare.com">Source</a>


## Whay headers could be deleted from TCP/IP packets?
Transport and payload can be deleted.


## Understanding Application Layer Protocols
 


<ul>
<li>HTTP and HTTPS</li>
<li>DNS</li>
<li>SMTP</li>
<li>POP|3</li>
<li>IMAP|4</li>
<li>SNMP</li>
<li>FTP</li>
<li>TFTP</li>
<li>SFTP</li>
<li>Telnet</li>
<li>SSH</li>
<li>SCP</li>
<li>NTP</li>
<li>LDAP</li>
<li>NetBIOS</li>
</ul>

## Network Storage Protocols
<ul>
<li>Fibre Channel 

    A technology that transmits data of up to 128 Gbps and uses
    special optical cables to connect the shared storage devices to servers

</li>

<li>iSCSI

    Internet Small Computer Systems Interface is an IP-based protocol used
    to communicate with storage devices.

</li>

<li>FCoE

    Fibre Channel over Ethernet is a protocol used to carry Fibre Channel
    commands over an Ethernet network in Ethernet frames. It is important to note that
    Fibre Channel runs at layer 2, so it is not routable across IP networks (whereas iSCSI
    is IP based, so it is routable

</li>

</ul>


## Complete list of HTTP Status Codes

|Status|Meaning|
| --- | --- | 

|1xx Informational 	 
|100| 	Continue|
|101| 	Switching protocols|
|102 |	Processing|
|103 |	Early Hints|
  	 
|2xx| Succesful |	 
|200| 	OK|
|201|	Created|
|202| 	Accepted|
|203|  	Non-Authoritative Information|
|204 |	No Content|
|205 |	Reset Content|
|206 |	Partial Content|
|207 |	Multi-Status|
|208 |	Already Reported|
|226 |	IM Used|
  	 
|3xx Redirection 	 
|300 |	Multiple Choices|
|301 |	Moved Permanently|
|302 |	Found (Previously "Moved Temporarily")|
|303 |	See Other|
|304 |	Not Modified|
|305| 	|Use Proxy|
|306 |	Switch Proxy|
|307 |	Temporary Redirect|
|308 |	Permanent Redirect|
  	 
|4xx Client Error 	 
|400 |	Bad Request|
|401 |	Unauthorized|
|402 |	Payment Required|
|403| 	Forbidden|
|404| 	Not Found|
|405 |	|Method Not Allowed|
|406 |	Not Acceptable|
|407 |	Proxy Authentication Required|
|408 |	Request Timeout|
|409 |	Conflict|
|410| 	Gone|
|411| 	Length Required|
|412| 	Precondition Failed|
|413| 	Payload Too Large|
|414| 	URI Too Long|
|415| 	|Unsupported Media Type|
|416| 	Range Not Satisfiable|
|417| 	Expectation Failed|
|418| 	I'm a Teapot|
|421| 	Misdirected Request|
|422| 	Unprocessable Entity|
|423| 	Locked|
|424| 	Failed Dependency|
|425| 	|Too Early|
|426| 	Upgrade Required|
|428| 	Precondition Required|
|429| 	Too Many Requests|
|431| 	Request Header Fields Too Large|
|451| 	Unavailable For Legal Reasons|
  	 
|5xx| Server Error 	 |
|500| 	Internal Server Error|
|501| 	Not Implemented|
|502| 	Bad Gateway|
|503| 	Service Unavailable|
|504| 	Gateway Timeout|
|505| 	|HTTP Version Not Supported|
|506| 	Variant Also Negotiates|
|507| 	Insufficient Storage|
|508| 	Loop Detected|
|510| 	Not Extended|
|511| 	Network Authentication Required|


## HTTP request methods

we have 6 methods of  HTTP request you find more from this <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods" >resource</a>

<ul>

<li>GET:

    The GET method requests a representation of the specified resource. Requests using GET should only retrieve data.

</li>

<li>HEAD:

    The HEAD method asks for a response identical to a GET request, but without the response body.

</li>

<li>POST:

    The POST method submits an entity to the specified resource, often causing a change in state or side effects on the server.

</li>

<li>PUT:

    The PUT method replaces all current representations of the target resource with the request payload.

<li>DELETE:

    The DELETE method deletes the specified resource.
</li>

<li>CONNECT:

    The CONNECT method establishes a tunnel to the server identified by the target resource.

<li>OPTIONS:

    The OPTIONS method describes the communication options for the target resource.

</li>

<li>TRACE:

    The TRACE method performs a message loop-back test along the path to the target resource.

</li>

<li>PATCH:

    The PATCH method applies partial modifications to a resource.

</li>

</ul>



## Identification
ways of identification before accessing sny resource.
<ul>
<li>Username </li>
<li>Smartcard</li>
<li>Token </li>
<li>Biometrics</li>
</ul>



## cryptography

<ul>
<li>symmetric cryptography</li>
<li>Asymmetric cryptography</li>
<li>Hashing</li>
</ul>


for more you can look <a href=" https://www.crypto101.io/Crypto101.pdf">Here</a>

## what is HSM? 



## Trusted Certificates

run in windows run <code>certmgr.msc</code> you can check certificates.

## Fuzzy Hashing



## phishing 

## Social Engineering 


# DDOS
