# Lab2 HTTP


1. Is your browser running HTTP version 1.0 or 1.1? What version of HTTP is the server running?

* http/1.1

2. What languages (if any) does your browser indicate that it can accept to the server?

* Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7

3. What is the IP address of your computer? Of the gaia.cs.umass.edu server?

* src = 192.168.8.105
* dst = 128.119.245.12

4. What is the status code returned from the server to your browser?

* status code = 304, which means use cached data

5. When was the HTML file that you are retrieving last modified at the server?

* If-Modified-Since: Fri, 19 Feb 2021 06:59:01 GMT

6. How many bytes of content are being returned to your browser?

* length = 305

7. By inspecting the raw data in the packet content window, do you see any headers within the data that are not displayed in the packet-listing window? If so, name one.

* Response Version: HTTP/1.1
* Status Code: 304
* Date
* Server:
* Connection: Keep-Alive
* ETag

8. Inspect the contents of the first HTTP GET request from your browser to the server. Do you see an “IF-MODIFIED-SINCE” line in the HTTP GET?

* No, since there is no cached data in browser

9. Inspect the contents of the server response. Did the server explicitly return the contents of the file? How can you tell?

* yes
  * status code = 200
  * Line-based text data: text/html (10 lines)

10. Now inspect the contents of the second HTTP GET request from your browser to the server. Do you see an “IF-MODIFIED-SINCE:” line in the HTTP GET? If
so, what information follows the “IF-MODIFIED-SINCE:” header?

* Yes, there is a "If-Modified-Since" header
* a descriptive time

11. What is the HTTP status code and phrase returned from the server in response to this second HTTP GET? Did the server explicitly return the contents of the file?Explain.

* status code = 304, Not Modified
* No content returned, the length of response is much smaller than the first response

12. How many HTTP GET request messages did your browser send? Which packet number in the trace contains the GET message for the Bill or Rights?

* only one http message send
* No.8

13. Which packet number in the trace contains the status code and phrase associated with the response to the HTTP GET request?

* No.14

14. What is the status code and phrase in the response?

* stauts code: 200
* Response Phrase: ok

15. How many data-containing TCP segments were needed to carry the single HTTP response and the text of the Bill of Rights?

* 4 tcp segments were send, to transfer a single http response

16. How many HTTP GET request messages did your browser send? To which Internet addresses were these GET requests sent?

* 3 GET request send
  * GET /ethereal-labs/lab2-4.html HTTP/1.1    128.119.245.12
  * GET /catelog/images/pearson-logo-footer.gif HTTP/1.1   165.193.123.218
  * GET /~kurose/cover.jpg HTTP/1.1   134.241.6.82

17. Can you tell whether your browser downloaded the two images serially, or whether they were downloaded from the two web sites in parallel? Explain.

* parallel, according to timestamp

17	7.305485	192.168.1.102	165.193.123.218	HTTP	625	GET /catalog/images/pearson-logo-footer.gif HTTP/1.1
20	7.308803	192.168.1.102	134.241.6.82	HTTP	609	GET /~kurose/cover.jpg HTTP/1.1
25	7.333054	165.193.123.218	192.168.1.102	HTTP	912	HTTP/1.1 200 OK  (GIF89a)
54	7.589877	134.241.6.82	192.168.1.102	HTTP	1096	HTTP/1.0 200 Document follows  (JPEG JFIF image)

18.  What is the server’s response (status code and phrase) in response to the initial HTTP GET message from your browser?

* 401 Authorization Required


19.   When your browser’s sends the HTTP GET message for the second time, what new field is included in the HTTP GET message?

a few seconds later

Authorization header was added
