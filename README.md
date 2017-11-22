#!/usr/bin/python
# -*- coding: UTF-8 -*-
import urllib
import urllib2
import re



user_agent = 'Mozilla/5.0 (Windows NT 6.1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/62.0.3202.94 Safari/537.36'
headers = { 'User-Agent' : user_agent }
 

url = 'https://www.zhihu.com/people/monyer/activities'
try:
    request = urllib2.Request(url, headers=headers)
    response = urllib2.urlopen(request)
    html = response.read()
except urllib2.URLError, e:
    if hasattr(e,"code"):
        print e.code
    if hasattr(e,"reason"):
        print e.reason

content_pattern = re.compile('', re.S)
content_list = re.findall(content_pattern, html)
for item in content_list:
    print item
