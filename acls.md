ACLs
======
 
 1. Create a second user on the system called "starbuck".  Open a second
    terminal window into the lab server connected as the user starbuck.
    Ensure you're working as a priviledged user (sudo) or root user
    while perofrming the lab. The starbuck user will be used to test
    setting the permissions.
    
        [root@localhost ~]# useradd starbuck; passwd starbuck
        Changing password for user starbuck
        New password:
        Retype new password:
        passwd: all authentication tokens updated successfully.

 2. Navigate into the /tmp directory and create two new directories named dir1 and dir2 and
    two files called file1 and file2
    
        [root@localhost tmp]# mkdir {dir1,dir2}; touch {file1,file2}

3. Idenity if any of the files currently have extended access control lists associated with them.

        [root@localhost tmp]# ls -l
        total 0
        drwxr-xr-x. 2 root root 6 May  5 20:00 dir1
        drwxr-xr-x. 2 root root 6 May  5 20:00 dir2
        -rw-r--r--. 1 root root 0 May  5 20:00 file1
        -rw-r--r--. 1 root root 0 May  5 20:00 file2

Note: The files have base ACLs but do not have extended ACLs. We know they do not have extended
ACLs because of no + at the end of the permissions listed.

4. Set an ACL for the starbuck user to read and write for file1

        [root@localhost tmp]# setfacl -m u:starbuck:rw file1
        [root@localhost tmp]# getfacl file1
        # file: file1
        # owner: root
        # group: root
        user::rw-
        user:starbuck:rw-
        group::r--
        mask::rw-
        other::r--

5. Set the mask on the file1 to read only, then as the starbuck user in your second terminal,
attempt to execute the following command echo "test" > /tmp/file1. Explain why this did not work.

        [root@localhost tmp]# setfacl -m m::r file1
        [root@localhost tmp]# getfacl file1
