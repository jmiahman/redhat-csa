Setting up SSH Authenication
======

1. Start two lab machines. This exercise will refer to the machines as server1 and desktop1.

2. Working as the user "student", on desktop1 generate a new RSA public and private key with a pass phrase of your choosing.

       [student@desktop1 ~]$ ssh-keygen 
       Generating public/private rsa key pair.
       Enter file in which to save the key (/home/student/.ssh/id_rsa): 
       Enter passphrase (empty for no passphrase): 
       Enter same passphrase again: 
       Your identification has been saved in /home/student/.ssh/id_rsa.
       Your public key has been saved in /home/student/.ssh/id_rsa.pub.
       The key fingerprint is:
       23:ef:49:53:15:37:48:24:68:43:e3:d3:e2:32:ac:0b student@desktop1.example.com
       The key's randomart image is:
       +--[ RSA 2048]----+
       |     ...o +O*    |
       |    + E. .oo+.   |
       |     o. .. + .   |
       |     .+. .E o o  |
       |    . * So o .   |
       |     .E..o. .    |
       |      . o. *     |
       |       .         |
       |         .       |
       +-----------------+

3. Copy the SSH key to server1.

       [student@desktop1 ~]$ ssh-copy-id student@server1

4. Try to remotely connect to server1 from desktop1 using the SSH keys.

       [student@desktop1 ~]$ ssh student@server1
       Agent admitted failure to sign using the key.
       student@server1's password:
       
5. Because we are using a passphrase with our ssh key and have not entered it,
   ssh is defaulting to the next available option in prompting for a user password.
   
   If you entered your password to login type:
   
          exit
   
   And that will reutrn you to the desktop1 prompt. If you have yet to enter your
   password you can return to the desktop prompt by pressing Ctrl + c

6. Now on desktop1, issue the correct commands to temporarily store the pass phrase 
   in your current shell session. This will prevent the ssh key from failing, or 
   depending on the ssh configuration, it may keep you from having to enter the 
   pass phrase each time you connect.

       [student@desktop1 ~]$ ssh-agent bash
       [student@desktop1 ~]$ ssh-add
       Enter passphrase for /home/student/.ssh/id_rsa: 
       Identity added: /home/student/.ssh/id_rsa (/home/student/.ssh/id_rsa) 
       [student@desktop1 ~]$ ssh student@server1
       Last login: Fri Nov  10 12:45:04 2020 from desktop1.example.com
       [student@server1 ~]$

6. Issue a remote command to create a directory named "test" on server1.

   First let's log out of server1:
   
       [student@server1 ~]$ exit
       logout
       Connection to server1 closed.
       [student@desktop1 ~]$
       
   Now let's run the remote command:
   
       [student@desktop1 ~]$ ssh student@server1 mkdir test
       
