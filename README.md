# HackRequests:
It is a dedicated requests lib that supports cookie, headers, get/post, etc. And it also supports rendering the response (e.g. Javascript, CSS, etc.) of GET requests by using PhantomJs enginee.

# Requirements:
## Install Selenium:
* sudo pip install -U selenium
* sudo apt-get install libfontconfig
 
## Install PhantomJs:
* For Linux 64-bit:
  * wget https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-x86_64.tar.bz2
  * tar -jxvf phantomjs-2.1.1-linux-x86_64.tar.bz2

* For Linux 32-bit:
  * wget https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-i686.tar.bz2
  * tar -jxvf phantomjs-2.1.1-linux-i686.tar.bz2

# Configuration:
Modify `self.executable_path` to the path of PhantomJS binary, e.g. `self.executable_path='/home/ubuntu/phantomjs-2.1.1-linux-x86_64/bin/phantomjs'`

# Usage:
```
import requests
import re
import time
from hack_requests import HackRequests

request_info = {} # It is a dict which contains all HTTP headers and data, the format is similar as Burp request.
request_info['protocol'] = 'http'
request_info['host'] = 'example.com'
request_info['path'] = '/iam/the/url?para=PARA'
request_info['user_agent'] = 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10.12; rv:45.0) Gecko/20100101 Firefox/45.0'
request_info['accept'] = '*/*'
request_info['accept_language'] = 'en-US,en;q=0.5'
request_info['accept_encoding'] = 'gzip, deflate'
request_info['referer'] = "http://example.com/"
request_info['cookie'] = "PHPSESSID=look_at_me_i_am_the_sessionid; Second_Cookie=i_am_second_cookie"
request_info['post_data'] = "para1=PARA1&para2=PARA2"

# Send GET request by using PhantomJS
r_get_p = HackRequests(request_info, 'PHANTOMJS').get_request() 

# Send GET request by using Requests
r_get_r = HackRequests(request_info).get_request()

# Send POST request by using Requests
r_post_r = HackRequests(request_info).post_request()
```
