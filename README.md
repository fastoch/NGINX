# NGINX

What is NGINX - https://www.youtube.com/watch?v=iInUBOVeBCc

## What is NGINX and why was it created?

### NGINX is a high performance web server  

Back in the days, when the Web was still simple and with less users, the basic use case was:
- a web browser requests a web page from one web server
- the web server assembles the page and sends it back to the browser
- the web browsers displays the page to the user

>[!important]
>a web server refers to both the physical machine and software running on the machine

Then, the Web became popular and you had millions of requests for the same website. 
- a single server couldn't cope with that amount of requests
- we need multiple servers to handle that load
- but which server will handle which request?

## What is NGINX used for?

### NGINX can also act as a **load balancer** 

- NGINX distributes incoming traffic across multiple backend servers
- it acts as a proxy server
- the way it distributes the load depends on the selected algorithm

Some **Load balancing methods** include:
- least connections: routes traffic to the server with the fewest active connections
- Round Robin: disrtibutes client requests in a sequential, cyclical manner to each server in the group

To recap, NGINX is:
- a Web server 
- a Proxy server
  - and the load balancing role is just one of the functionalities of NGINX Proxy.

## What are NGINX other features?

### Caching

Caching is a core feature of NGINX Proxy:
- Fetching data from remote servers or databases on each request results in slower response times.  
- Instead, we want to assemble the page content once and store the response
- the idea is to keep one file copy and send it to every one who requests it

NGINX as a proxy server allows you to cache responses from backend server for frequently accessed resources.

### Minimizing the attack surface

- Each publicly exposed server represents an entry point that attackers can target
- instead of having to secure each and every server, the idea is to have only one server publicly accessible
  - having a single entry point (the NGINX proxy server) increases the security
  - this also allows for centralized access control, and centralized logging & monitoring

### Encrypted communication

- Since we only have one entry point, we can focus all our efforts to securing that one proxy server in all aspects.
- One important security measure is **encrypted communication**
- NGINX can handle TLS encryption and decryption
- front-end will send encrypted data to the proxy
- the NGINX proxy server will forward the data to the web server
- the web server will decrypt the data
- you can configure your proxy to deny non-encrypted requests

### Compression

- NGINX proxy can also compress the response to reduce bandwidth usage and improve load times
- 
- 

@7
