### DNS

Domain Name system is the system that translates/maps ***Domain Names*** to their corresponding ***IP addresses***.

<img src="/Users/morris/Downloads/how-route-53-routes-traffic.8d313c7da075c3c7303aaef32e89b5d0b7885e7c.png" alt="how-route-53-routes-traffic.8d313c7da075c3c7303aaef32e89b5d0b7885e7c" style="zoom:75%;" />

DNS is hierarchical, meaning it is layered. The one on the top is the root name server. It keeps track of all the Top Level Domain Servers, which are those with Domain Name like ".com", ".org" and ".ca".  Below them are the Authoratative Domain Name servers (companies, government, orginaztions or individuals). 

When we would like to access a website and we type its link in the browser, the iterative DNS resolver 	will do the work for you. It first searches its local cache. Its cache is temporay and will expire by the way. If no record is found, then it goes talk to root server who then gives the address of the corresponding TLD server to the resolver. This process repeats between TLD and AND servers, and after all these hustles, we get the address of the site we wish to visit. The browser uses the address to pull webpage and then calls it a day!