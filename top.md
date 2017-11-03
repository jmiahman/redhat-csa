Running Top
======

1. Run this command in your bash shell

       [root@localhost]# (while true; do echo -n "My program" >> ~/output.file; done) &
       [1] 22477
   
   Take note of the process id (or PID) of the background process (the above PID is just an example)

2. Start the top program.

       [root@localhost]# top

3. The top program shows all running processes on the system but sorts them. Using your keyboard, browse up and down to view the processes.

   Use the keyboard up and down arrows to navigate

4. Sort all processes by memory percentage.

       shift + m

5. Sort all processes by CPU usage.

       shift + p

6. Renice the process for the command started at the beginning of the exercise. The command will be  "bash" displayed in the top program. Set the nice level to -20.

   Press the "r" key, enter the process id of the process you want to renice, and set the nice level.

6. Kill the bash command using top.

   Press the "k" key and enter the process id to kill then press enter.
