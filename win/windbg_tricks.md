#WinDbg Tricks
--------------------------------

某些情况下需要**跟踪指令流**，即查看从当前指令位置运行到目标指令位置执行过的所有指令，可以：
```
/*
假设: 目标指令地址为TADDR;
用法：当前WINDBG输入是因为触发断点(bp/ba/bm等命令)，从此断点位置可以执行到TADDR位置，该过程中当前线程不会终止。
*/
.logappend /u d:\logs.txt
.for(;@$ip-TADDR;){u @$ip l1;t} 

例如:
32位Windows环境: .for(;@$ip-00093c69;){u @$ip l1;t}  
64位Windows环境: .for(;@$ip-00000000`00093c69;){u @$ip l1;t}
```
