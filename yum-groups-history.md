YUM Groups & History
======

1. List available groups.

       [root@localhost ~]# yum group list

2. List all packages that belong to the "Security Tools" group. When looking at this, what packages will be installed?

       [root@localhost ~]# yum group info "Security Tools"

3. Install the "Security Tools" group.

       [root@localhost ~]# yum group install "Security Tools"

4. Undo the install of the "Seccurity Tools" group.

       [root@localhost ~]# yum history
       Loaded plugins: amazon-id, rhui-lb
       ID     | Login user               | Date and time    | Action(s)      | Altered
       -------------------------------------------------------------------------------
           17 |                    | 2015-05-02 11:10 | Install        |    3   
           16 |                    | 2015-05-02 10:55 | Erase          |    1   
           15 |                    | 2015-05-02 10:51 | Install        |    5   
       [root@localhost ~]# yum history info 17
       Loaded plugins: amazon-id, rhui-lb
       Transaction ID : 17
       Begin time     : Sat May  2 11:10:49 2015
       Begin rpmdb    : 666:2f8b0d9de8e03b35809bb3623696ba61ab589deb
       End time       :            11:10:51 2015 (2 seconds)
       End rpmdb      : 669:84e7861867838346e3c843a204e1ad2b5a0cc4ba
       User           :  
       Return-Code    : Success
       Command Line   : group install Security Tools
       [root@localhost ~]# yum history undo 17
