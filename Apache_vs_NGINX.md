src = https://www.youtube.com/watch?v=9nyiY-psbMs&t=54s

---

# What happens when using a web app 

- The Web browser (client) sends HTTP requests through the Internet
- Nginx/Apache receives those requests and sends thems to one of the backend servers hosting our web app
- The backend server gathers the resources requested by the the web browser and sends them to Nginx/Apache
- Nginx/Apache sends the backend server response to the Web browser

# They're both...

- Free & Open Source Software (FOSS)
- commonly used as **Web servers** and reverse **proxy servers**
- often used as 7 layer **load balancers**, meaning they operate at the application layer, specifically HTTP

# Their advantages

- LOAD BALANCING: 
  - we can have as many backend servers as we need to fit the number of requests
  - and the requests will be routed to the least busy of them, which increases performance and availability
- SECURITY:
  - never expose our backend servers directly to the public Internet
  - the outside world "believes" it's the proxy that processes the requests and sends the responses
- CACHING:
  - a proxy server can cache some of the resources, and then it can serve them up on its own
  - this feature is saving time and network throughput
- COMPRESSION:
  - happens between the proxy server and the client (the web browser)
  - decreases load times
 
# They're different because...

- Nginx is faster
- Nginx is easier to configure
- Nginx is better suited when you need to handle simple static files
- Nginx is more popular in the container space (Docker & K8s)
- Apache is better at handling dynamic content
- You can do a lot more with Apache, albeit at the expense of speed in some cases

---

# They don't need to fight

It's entirely possible to have Nginx as acting as your reverse proxy with several Apache web servers behind it, or vice versa.

---
EOF

