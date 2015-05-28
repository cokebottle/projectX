#This script checks the response of a webpage depending on the user agent
#This is useful for CTFs where you get a link and the response depends on the user agent
#Basic auth is included

import urllib
import hashlib
import urllib2
from xml.dom import minidom

xmldoc = minidom.parse('useragent.xml')
useragents = xmldoc.getElementsByTagName('useragent')

url = [your url]
username = [username]
password = [password]

print "Working ... "

for i in range (0,len(useragents)):
    user_agent = useragents[i].attributes['useragent'].value
    password_mgr = urllib2.HTTPPasswordMgrWithDefaultRealm()
    password_mgr.add_password(None, url, username, password)
    handler = urllib2.HTTPBasicAuthHandler(password_mgr)

    opener = urllib2.build_opener(handler)
    opener.addheaders = [('User-agent', user_agent)]

    f = opener.open(url)
    m = hashlib.sha224(f.read()).hexdigest()

    if m != [hash of page we don't want]:
        print "Got a hit: " + user_agent
        print "Hash value: " + m
        print "HTML Page: "
        f = opener.open(url)
        print f.read()
