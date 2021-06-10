# Web-Crawler

This is a simple Web Crawler developed in Python using Mercator scheme. The code is in ``WebCrawler.ipynb`` file.

## 1. URL Frontier
The URL frontier is a structure of front queues and back queues. When the crawler starts for the first time, URL frontier contains the following seed URLs.

https://docs.oracle.com/en/<br />
https://www.oracle.com/corporate/<br />
https://en.wikipedia.org/wiki/Machine_learning<br />
https://www.csie.ntu.edu.tw/~cjlin/libsvm/index.html<br />
https://docs.oracle.com/middleware/jet210/jet/index.html<br />
https://en.wikipedia.org/w/api.php<br />
https://en.wikipedia.org/api/<br />
https://en.wikipedia.org/wiki/Weka_(machine_learning)<br />

The process is multithreaded. Each thread requests a URL from frontier when required. The process of getting data from threads while maintaining politeness and 
moving data from F-queues to B-queues is done according to the Mercator scheme. Prioritizer function is a stub function. URLS that go out of frontier maintained in a list. 
Newly encountered URL’s are en-queued after passing through URL filtering and Dup-URL elimination module. For this project we wait for 15 to 20 seconds after sending one request to send another request.

## 2. Fetch
After getting one URL from frontier, we retrieve its content from the webserver.

## 3. Parse
Now we parse the content of the fetched page and retrieve all the URLS from it.

## 4. URL Filter
We filter the URLs, received from parser, that are restricted from its webserver. The restricted page/s are given in robot.txt file.

## 5. Duplicate URL Elimination
After filtering restricted URLS, we check if the newly extracted URLs are already crawled or not. The URLS that pass this test are added to the frontier.

## 6. Stopping the process
We stop the process based on number of URLs, for example we stop when we have crawled 100 URLs
