# NGINX

What is NGINX - https://www.youtube.com/watch?v=iInUBOVeBCc  
Official documentation: https://nginx.org/en/docs/beginners_guide.html 

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

---

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

### Compression & Segmentation

- NGINX proxy can compress the response to reduce bandwidth usage and improve load times
- NGINX also supports segmentation, which means one big file can be segmented into multiple chunks

---

## NGINX configuration

- the main config file is typically named `nginx.conf` and is usually located in the `/etc/nginx/` folder
- to set up the server's behavior, we need to use a custom syntax comprising **directives** and **blocks**
- this is where we will define whether we want our NGINX server to be a web server, or a proxy server
- we do that by configuring:
  - whether it should forward the traffic to other web servers,
  - or whether it should be serving the files itself

### NGINX as a Web server

- you can configure which port you want your nginx server to listen on
- the "location" directive defines how the server should process specific types of requests
- in there, you need to specify the location that contains your files
  
![image](https://github.com/user-attachments/assets/10c2c66e-fa5e-4f12-9a6f-f65fa5eea37d)

But, as we learnt, communicating on port 80 (HTTP) is insecure and we want to encrypt all communication.  
- to configure that in NGINX, we tell the http server to route any traffic coming on port 80 to the HTTPS endpoint
- and then we configure the https server so it serves content over HTTPS with SSL/TLS configured
- this https server needs to know:
  - the location of the files it will serve
  - the location of the SSL/TLS certificates (public and private keys)

![image](https://github.com/user-attachments/assets/498d03a1-eb9f-4480-915f-d77fcf3dfdae)

### NGINX as a Proxy server

- Here's an example of how to configure nginx as a load balancer:
![image](https://github.com/user-attachments/assets/fdc712f6-edb1-4ddb-8ecf-7e52bceed157)

- and within that configuration, you can also define which load balancing algorithm you want to use:
![image](https://github.com/user-attachments/assets/7727c6d2-153b-40c3-94e2-47a913cc05a8)

### Enabling the caching of responses (on the proxy server obviously)

The caching configuration includes multiple elements like:
- how long the cache should be stored before it's refreshed 
- 

![image](https://github.com/user-attachments/assets/c9ca6bb1-2e31-490b-bce9-a48d3415edec)  

---

## NGINX as a Kubernetes Ingress Controller

### What is an Ingress controller?

- it's a specialized load balancer for managing ingress (incoming) traffic in K8s (Kubernetes)
- what NGINX does for web servers can also be done for a K8s cluster in the form of an ingress controller
- nginx acts as a proxy and load balancer that receives incoming traffic and forwards it to the right service inside the cluster 
- this traffic forwarding is based on rules defined in an ingress resource

![image](https://github.com/user-attachments/assets/bb4ae1fd-9c44-4c5c-8290-e94a0d38bcab)

There are actually many ingress controller implementations out there for K8s, but NGINX is one of the most popular.

### NGINX load balancer VS Cloud load balancer

You may be thinking: "Doesn't each cloud platform have its own load balancer? Why do I need nginx as a load balancer?"  
- You actually need both
- Nginx ingress controller acts as a load balancer inside the K8s cluster 
- since the Nginx ingress controller lives inside the K8s cluster, it is not publicly accessible
- the public entry point for the browser requests is the Cloud load balancer
- the Cloud load balancer forwards the requests to the Nginx ingress controller
- the Nginx ingress controller will then forwards the requests internally to the appropriate K8s service

![image](https://github.com/user-attachments/assets/adc30476-2fa2-4288-8649-0491370dfccf)  

- this way, the cluster component is **never directly exposed** to public access

---

## NGINX vs Apache

- Apache was released in 1995 (like JavaScript)
- Nginx was released in 2004
- They are both widely used with the same functionalities
- The major benefit of Nginx is that it's faster and more lightweight

![image](https://github.com/user-attachments/assets/73e82df3-75e8-485d-bc0a-482548bf0d7a)



