# 6.4.2.2  Recommendation

To solve this problem, it is required to separate the Webpages from the web API’s and make it run on different servers. Once completed, the Angular Universal can be implemented which uses server side rendering \(SSR\). This will allow web crawlers to detect the site by executing javascript code along with producing complete html at the server. Implementing Angular universal is a tradeoff though as it creates another dependency on outside technology and SSR is not ideal and defeats some of the purpose of using a SPA.

