# Lab1 - Introduction

1. List 3 different protocols that appear in the protocol column in the unfiltered packet-listing window in step 7 above.
    * TCP
    * DNS
    * HTTP
    * TLSv1.3

2. How long did it take from when the HTTP GET message was sent until the HTTP OK reply was received?
   (By default, the value of the Time column in the packetlisting window is the amount of time, in seconds, since Wireshark tracing began.
   To display the Time field in time-of-day format, select the Wireshark View pull down menu, then select Time Display Format, then select Time-of-day.)
    * 5.512649 - 5.175985
    * HTTP/1.1 304 Not Modified
      * client 在发送 request 的时候，发现有相应请求 url 的缓存，就会在 header 里面添加 If-Modified-Since 字段，含有相应的时间
      * server 在收到含有 If-Modified-Since 字段的 request 之后，判断相应的数据是否发生过改变，如果没有，那么就返回 304，并且不携带任何数据。
      * client 在收到了 response 之后，知道自己的数据并没有过期，即可直接使用。
      * 这一过程，能够减少数据传输量，提升传输效率。

3. What is the Internet address of the gaia.cs.umass.edu (also known as wwwnet.cs.umass.edu)? What is the Internet address of your computer?
    * Source：192.168.8.105
    * Destination：128.119.245.12

4. Print the two HTTP messages (GET and OK)
    * GET：

GET /wireshark-labs/INTRO-wireshark-file1.html HTTP/1.1
Host: gaia.cs.umass.edu
Connection: keep-alive
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 11_1_0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.146 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
If-None-Match: "51-5bbaafca66abc"
If-Modified-Since: Fri, 19 Feb 2021 06:59:01 GMT

    * OK

HTTP/1.1 304 Not Modified
Date: Fri, 19 Feb 2021 08:25:40 GMT
Server: Apache/2.4.6 (CentOS) OpenSSL/1.0.2k-fips PHP/7.4.14 mod_perl/2.0.11 Perl/v5.16.3
Connection: Keep-Alive
Keep-Alive: timeout=5, max=100
ETag: "51-5bbaafca66abc"
