# 6.4.2.1  Technical Debt

  
Teammates adopted the Single Page Application \(SPA\) architecture in designing the frontend. The decision of implementing SPA architecture using Angular version 7 has caused a challenge in terms of friendliness on SEO. Angular v7 is usually rendered on the client side which prevents web crawlers and search engines from seeing the complete structure and contents of the website \[6\]. Being visible to the public and acquiring users through search engines is important to Teammates business goals. With the growing use of angular, the solution has been developed to solve this named Angular Universal. But based on the teammate’s frontend design, there is the problem for using Angular Universal with teammates. The trade-off here is that Universal can run only in Node.js and it requires webpage files and web API’s to run on different servers.

