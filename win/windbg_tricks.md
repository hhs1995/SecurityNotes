#WinDbg Tricks
--------------------------------

某些情况下需要**跟踪指令流**，可以这样：
```
.logappend /u d:\logs.txt
.for(;$ip-00093c69;){u $ip l1;t}  或64位下 .for(;$ip-00000000`00093c69;){u $ip l1;t}
```
