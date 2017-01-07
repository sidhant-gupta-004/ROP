# ROP
###A discussion and collection of the basic (and hopefully sometime, advanced) concepts in ROP.

Source Code for problems rop(1-4) available on https://github.com/picoCTF/2013-Problems. These 4 problems were taken from picoCTF 2013.

###rop1
Here, we are supposed to simply change the return address of vulnerable_function() to the base address of not_called(). I am, of course, working on more complex problems, hope to upload them and their payloads soon! :)

###rop
Here, the aim of course is to get a shell, and that is done by invoking system@plt. To make things easy, however, the question has given the location of the string containing '/bin/sh' in the program itself.

###rop3
Here, what we had to do is simple. The program contains neither system() nor /bin/sh. BUT, the system function exists in the GOT table and the the /bin/sh string shows up on doing `find /bin/sh` on GDB. However, these are both in the ASLR region and their addresses need to be calculated with respect to the address of another function: here, read(). Then, system is simply called with /bin/sh as argument. Cake. :)

###rop4
This one I can argue, is the simplest. We just have to find the address of /bin/sh, which is a `find` away after crashing the program, and then put that into the function execlp(), as provided in the C-code source file.

###ropasaurusrex
This one is from Plaid CTF 2013. Here, we have to everything by ourselves: find address of read(), calculate address of system() from it, then write /bin/sh somewhere (writeable, duh) in the program (I chose the .dynamic section), and then call system with /bin/sh as argument. My first tutorial problem in ROP.
