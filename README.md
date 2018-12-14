# cd-Command-Set-Mode-Query-Mode
 Uing cd command Windows command line, can't navigate to D:\

It's not like Unix or Linux shell program. 
The cd command in Microsoft's command interpreter doesn't behave as the cd commands in such shells do.It behaves somewhat differently. 
In particular, it doesn't always change directory. In Unix and Linux shells, cd only ever sets the working directory. 
In Microsoft's command interpreter, cd sometimes queries it. There's no separate pwd command, so cd does two jobs.
If you give it no arguments, or an argument that is just a drive letter and a colon without a path, then it reports the current directory instead of changing it. 
If you give it no arguments, it reports the current directory of the current drive of the command interpreter process. 
If you give it only a drive letter and a colon as an argument, it reports the command interpreter process' current directory of that drive. 
Each drive has its own current directory in the command interpreter. 
This is a fiction maintained by the run-time libraries for Microsoft's and several other vendors' implementations of various programming languages. 
Win32 itself doesn't work this way.
So when you gave it d: as an argument, it reported the the command interpreter process' current directory on drive D to you, which happened to be D:\. 
If you'd given it no arguments at all, it would have reported C:\ to you.
If you want the cd command to always be in set mode and never be in query mode you need to add the /D option to it. 
This forces the command to always be in set mode, and also extends it so that it changes the current drive as well as changing a drive's current directory. 
In other words, it works more like the underlying Win32 API actually does.
