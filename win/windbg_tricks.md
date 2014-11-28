#WinDbg Tricks
--------------------------------

某些情况下需要**跟踪指令流**，可以这样：
```
.logappend /u d:\logs.txt
.for(;$ip-00093c69;){u $ip l1;p}
```
