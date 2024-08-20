# NGINX
What is NGINX - https://www.youtube.com/watch?v=iInUBOVeBCc

## What is NGINX?

**NGINX is a high performance web server**  

Back in the days, when the Web was still simple and with less users, the basic use case was:
- a web browser requests a web page from one web server
- the web server assembles the page and sends it back to the browser
- the web browsers displays the page to the user

>[!important]
>a web server refers to both the physical machine and software running on the machine

## Why was NGINX created?

Then, the Web became popular and you had millions of requests for the same website. 
- a single server couldn't cope with that amount of requests
- we need multiple servers to handle that load
- but which server will handle which request?

Besides being used as a web server, NGINX can also act as a **load balancer**. 
- NGINX distributes incoming traffic across multiple backend servers
- it acts as a proxy server
- the way it distributes the load depends on the selected algorithm

Some Load balancing methods include:
- least connections: routes traffic to the server with the fewest active connections
- 

## What is NGINX used for?
