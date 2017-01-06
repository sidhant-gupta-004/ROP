# ROP

###rop1
Here, we are supposed to simply change the return address of vulnerable_function() to the base address of not_called(). I am, of course, working on more complex problems, hope to upload them and their payloads soon! :)

###rop2
Here, the aim of course is to get a shell, and that is done by invoking system@plt. To make things easy, however, the question has given the location of the string containing '/bin/sh' in the program itself.
