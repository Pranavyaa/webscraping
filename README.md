import re
import urllib.request, urllib.parse, urllib.error
from bs4 import BeautifulSoup
import ssl

ctx = ssl.create_default_context()
ctx.check_hostname = False
ctx.verify_mode = ssl.CERT_NONE

 
url = input('Enter - ')
html = urllib.request.urlopen(url, context=ctx).read()
soup = BeautifulSoup(html, 'html.parser')
lst=soup.find_all("a",string="Principal")
#print(lst)

for i in lst:
    s=i.get('href')

#print(s)
url = url+s
#print(url)
html = urllib.request.urlopen(url, context=ctx).read()
soup1 = BeautifulSoup(html, 'html.parser')
lst1=soup1.find_all('p')
for j in lst1:
    if(j.string == None):
       continue
    
    print(j.string)

