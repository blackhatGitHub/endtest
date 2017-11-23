#!/usr/bin/python
# -*- coding: UTF-8 -*-
import urllib
import urllib2
import re



user_agent = 'Mozilla/5.0 (Windows NT 6.1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/60.0.3112.113 Safari/537.36'
headers = { 'User-Agent' : user_agent }
 

url = 'http://www.chinahr.com/sou/?city=36%2C400&keyword=%E7%BD%91%E7%BB%9C%E5%AE%89%E5%85%A8%E5%B7%A5%E7%A8%8B%E5%B8%88'
try:
    request = urllib2.Request(url, headers=headers)
    response = urllib2.urlopen(request)
    html = response.read().decode('utf-8')
except urllib2.URLError, e:
    if hasattr(e,"code"):
        print e.code
    if hasattr(e,"reason"):
        print e.reason

#content_pattern = re.compile('<span class="e1">.*?<a href=".*?" onclick=".*?" target=".*?">(.*?)</a>', re.S)
content_pattern = re.compile('<span class="e1">.*?>(.*?)</a>', re.S)
content_list = re.findall(content_pattern, html)
for item in content_list:
    print item
