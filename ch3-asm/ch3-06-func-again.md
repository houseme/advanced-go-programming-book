# 3.6. 再论函数(Doing)

在前面的章节中我们已经简单讨论过Go的汇编函数，但是那些主要是叶子函数。叶子函数的最大特点是不会调用其他函数，也就是栈的大小是可以预期的，叶子函数也就是可以基本忽略爆栈的问题（如果已经爆了，那也是上级函数的问题）。如果没有爆栈问题，那么也就是不会有栈的分裂问题；如果没有栈的分裂也就不需要移动栈上的指针，也就不会有栈上指针管理的问题。但是是现实中Go语言的函数是可以任意深度调用的，永远不用担心爆栈的风险。那么这些近似黑科技的特殊是如何通过低级的汇编语言实现的呢？这些都是本节尝试讨论的问题。

TODO