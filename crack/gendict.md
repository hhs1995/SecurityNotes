#Simple Dictionary Generate
-------------------------
```python
f=open("dict.txt",'w+')

chars=[
'0','1','2','3','4','5','6','7','8','9',
 'a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z',
 'A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z',
]

pwdlen = 6
base=len(chars) #62
end=len(chars)**pwdlen

for i in range(0,end):
	n=i
	pwd = ""
	for c in range(0, pwdlen):
		pwd = chars[n%base]+pwd
		n=n/base
	print i,pwd
	f.write(ch3+ch2+ch1+ch0+'\n')

f.close()
```
