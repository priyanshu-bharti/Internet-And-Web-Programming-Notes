# # Internet and Web Programming (ITA6003)
## Module 1 : Basics of Internet
- [x] Internet working
- [x] How HTTP Works
- [x] IPv4 Header
- [x] IPv6 Address
- [x] Web Clients 
- [x] Web Servers
- [x] Basic Internet Protocols
- [x] How API Works
- [x] Domains
- [x] URIs and URLs
- [x] Applications of Internet
- [x] Types of Networks
- [x] Web Browser
- [x] Web Caching

## Internet
* The Internet is not the same as the Web. 
* The Internet is bigger, older, and more varied.
* It was invented in 1969 to connect computers across the US. Nowadays, _billions_ of devices (including PCs, laptops, mobile phones, TVs, fridges…) are **interconnected**.

### Client and Server
* Usually, a connection on the Internet takes place between **2** computers only:
	* One that **has** the information (the _server_)
	* One that **wants** it (the _client_).
* A **client** is a program that can take up many forms:
	* a Web browser (like Firefox)
	* an email client (like Outlook)
	* a messenger app (like WhatsApp)
	* a video streaming service (like Netflix)
* Each of these programs will retrieve information from a **server**, where some resource is stored (a website, emails, messages, movies).
* Although client programs also send information to the server, clients usually don’t store information, while servers do.
* A **server** can be considered a _dedicated_ computer always connected to the Internet, whose sole purpose is to **deliver** content.

### Internet Protocol (IP)
* Set of rules that defines the routing and addressing of packets
* Packets are data divided into smaller chunks
* IP information of the sender and receiver is attached to each packet
* Routers are used to send packets at the right place.
* Once the data arrives at the destination, it is handled differently based on which transport protocol is used.
* IP address is a unique identifier for a device which is connected to the internet.
* Each IP is a series of decimal or hex digits separated either by a dot or a colon. 

### IPv4
* IPv4 is a version 4 of IP introduced in 1983.
* It is a current version and the most commonly used IP address. 
* It is a 32-bit address written in four numbers separated by dots. 
* This address is unique for each device. 
* For example, **66.94.29.13**.
* The IPv4 consists of four sets, and these sets represent the octet.
* Each number in an octet is in the range from 0-255. 

### IPv4 Header
1. `Version.` : 4-bit version indicator. set to 0100.
2. `Internet Header Length.` : How many 32 bit words present in header
3. `Type of Service.` : Quality of the packets (for VoIP and more).
4. `Explicit Congestion Notification.` : Send/Get congestion notifications.
5. `Total Length.` : Total length of the field size
6. `Identification.` : Unique ID for a packet
7. `Flags.` : Determine the packet’s fragmentation
8. `Fragment Offset` : Where the fragmentation starts
9. `Time to live.` : How long will a packet last in the internet.
10. `Protocol.` : TCP / UDP
11. `A checksum of header.` : Checksum for detecting any errors.
12. `Source Address.` : IP address of sender
13. `Destination Address.` : IP address of receiver
14. `Options.` : Other things related to security.

### IPv6
* IPv6 is a 128 bit address
* It is an alphanumeric address consisting of 8 fields separated by a colon.
* Doesn’t contain classes of IP addresses.
* Hexadecimal address
* Provides encryption and authentication.

## HTTP
* HTTP stands for **HyperText Transfer Protocol**.
* Used to access the data on the World Wide Web (www).
* Data can be plain text, hypertext, audio, video, and so on.
* Allows rapid jumps from one document to another document.
* Similar to FTP as it also transfers the files from one host to another host. 
* HTTP is a connectionless protocol. 
* HTTP client initiates a request and waits for a response from the server. 
* The connection between client and server exist only during the current request and response time only.
* HTTP protocol is a media independent as data can be sent as long as both the client and server know how to handle the data content. 
* HTTP is a stateless protocol as both the client and server know each other only during the current request. 
* Due to this nature of the protocol, both the client and server do not retain the information between various requests of the web pages.

### Domains
* It is the location of the website
* It is mapped to the IP address of the server hosting the website
* Convenient way of remembering a website rather than IP addresses.
* Can be maximum 63 characters.
* **Subdomains** : Unique URL that extends the existing domain from the front.
* Ex : Domain - google.com, subdomain - docs.google.com
* Directories are folders inside the domain which might contain some resource.
* Ex : apple.com/in

### URLs
* Uniform Resource Locator
* It provides the location and mechanism of retrieving a resource
* It is sometimes called the address of the website.
* It consists of:
	* Protocol
	* Subdomain
	* Domain and domain-suffix
	* Directories
	* Webpage
* It is mainly used to search the webpages on the internet.

### URIs
* Reference to the addresses, names or objects.
* URL and URN are examples of URIs.
* Stands for Uniform Resource Identifiers.
* A URI contains scheme, authority, path, query, and a fragment. 
* It is commonly used in XML and tag library files such as JSTL and XSTL to identify the resources and binaries.

### How API works
* Stands for Application Programming Interface
* API communicates with the program for us.
* Programmers expose API endpoints which can be used to make an API call.
* APIs consist of 3 things : **User** (Making the requests), **Client** (Computer sending the request to the server), **Server** (Computer responding to the requests).
* The first step is to make an API call using an endpoints.
* The server can respond to 4 actions: **GET** (retrieve information), **POST** (Make a new information entry), **PUT** (Updates existing information), **DELETE** (Deletes existing information).
* Server then processes the request and returns a response (often in the form of JSON or XML which can be parsed by any programming language).

### Basic Internet Protocols
1. **FTP** : File Transfer Protocol - File transfer
2. **SMTP** : Simple Mail Transfer Protocol -  Sending Emails
3. **IMAP** : Internet Message Access Protocol - Receiving Emails
4. **IRC** : Internet Relay Chat - For online chats
5. **HTTP** : HyperText Transfer Protocol - Browsing between Websites.
6. **UDP** : User Datagram Protocol - Streaming audio and videos
7. **TCP** : Transmission Control Protocol - Accessing a webpage.

### Types of Networks
* **LAN (Local Area Network)** 
	* Spans a relatively small area. 
	* Confined to a single room, building or group of buildings
	* One LAN can be connected to other LANs over any distance via telephone lines and radio waves. 
* **WAN (Wide Area Network)**
	* Large geographical area, generally having a radius of more than 1 km
	* WAN consists of two or more local-area networks (LANs).
	* Computers connected to a wide-area network are often connected through public networks, such as the telephone system
	* They can also be connected through leased lines or satellites.
* **MAN (Metropolitan Area Network)**
	* Interconnects users with computer resources in a geographic area or region larger than that covered by even a large local area network (LAN) but smaller than the area covered by a wide area network (WAN) 

### Applications of Internet
* **WWW**
	* World Wide Web is also known as Web.
	* It is a collection of websites or web pages stored in web servers and connected to local computers through the internet. 
	* These websites contain text pages, digital images, audios, videos, etc. 
	* Users can access the content of these sites from any part of the world over the internet using their devices such as computers, laptops, cell phones, etc. 
	* The difference between internet and WWW is that internet encompasses everything from enabling users to access files, chatting or calling other people, and more whereas WWW involves browsing the webpages and jumping from one to another page.

* **Electronic Mail (Email)**
	* Email is the short form of electronic mail. 
	* It is one of the ways of sending and receiving message(s) using the Internet. 
	* An email can be sent anytime to any number of recipients at anywhere. 
	* The message can be either text entered directly onto the email application or an attached file (text, image audio, video, etc.) stored on a secondary storage. 
	
* **Chat**
	* Chatting or Instant Messaging (IM) over the Internet
	* Two individuals can also send messages instantly. 
	* With ever increasing internet speed, it is now possible to send image, document, audio, video as well through instant messengers. 
	* We can have group chat or group calls. 
	* Ex: WhatsApp, Slack, Skype, Yahoo Messenger, Google Talk, Facebook Messenger, Google Hangout, etc.

* **VoIP**
	* Voice over Internet Protocol or VoIP, allows us to have voice call (telephone service) over the Internet, i.e., the voice transmission over a computer network rather than through the regular telephone network. 
	* It is also known as Internet Telephony or Broadband Telephony. 
	* But to avail the phone service over the Internet, we need to have an Internet connection with reasonably good speed. 

### Web Browser
* It is a software that can open the webpages (HTML Documents in a readable format while preserving the HyperText Links)
* It is required to access the internet.
* There are many kinds of web browsers based on different technology. 
* Ex: Chrome, Edge and Safari based on Apple’s Webkit Engine; Firefox, Epiphany and more based on Quantum.

### Web Caching
* HTTP supports proxy servers
* Proxy servers store the objects which are requested frequently.
* If there is a resource that is rarely required, it is requested from the origin rather than proxy server.
* Caching improves speed and latency by decreasing traffic to the origin server.
* Web caches periodically pull the resources from the server. Whenever a copy of resource is modified, a push request to modify that resource is sent.
