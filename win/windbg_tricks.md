#WinDbg Tricks
--------------------------------
## 1.符号问题
解决Winfbg符号问题请参考微软知识库文章：
(《使用 Microsoft Symbol Server 获取调试符号文件》)[http://support.microsoft.com/kb/311503]

## 2.跟踪指令流
某些情况下需要**跟踪指令流**，即查看从当前指令位置运行到目标指令位置执行过的所有指令，可以：
```
/*
假设: 目标指令地址为TADDR;
条件：当前WINDBG的命令输入状态是因为触发断点(bp/ba/bm等命令)，从此（断点）位置执行到目标地址TADDR的过程中当前线程不会终止。
*/
.logappend /u d:\logs.txt
.for(;@$ip-TADDR;){u @$ip l1;t} 

例如:
32位Windows环境: .for(;@$ip-00093c69;){u @$ip l1;t}  
64位Windows环境: .for(;@$ip-00000000`00093c69;){u @$ip l1;t}
```
