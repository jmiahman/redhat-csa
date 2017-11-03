Authenticating CentOS to a Active Directory Server
======

Optional, check for updates.
     
     yum -y upgrade

1. Check network access to AD Server.
     
       ping ad.server.com

2. Install needed Packages.
     
       yum -y install realmd oddjob oddjob-mkhomedir sssd adcli samba-common

3. The realm discover command returns complete domain configuration and a 
   list of packages that must be installed for the system to be enrolled in the domain.

       realm discover ad.server.com
   
   By default, the join is performed as the domain administrator. For AD, the 
   administrator account is called Administrator; for IdM, it is called admin. 
   To connect as a different user, use the -U option:
      
       realm join ad.server.com -U 'AD\user'
     
4. To enable access for specified for all users within the configured domain to access 
   the local system:
   
       realm permit --realm ad.server.com --all
      
5. Now test whether the system was successfully enrolled into a domain, by verifying that you can 
   log in as a user from the domain and that the user information is displayed correctly:
   
        id user@ad.server.com
   
   if configured correctly should return something similiar to:
   
        uid=1448701303(user@ad.server.com) gid=1348701516(domain group@ad.server.com) 
        groups=1348701516(domain group@ad.server.com)

  6. To test using ssh, use something similiar to:
  
         ssh -l user@ad.server.com linux-client.ad.server.com
        
     if configured correctly this will return something similiar to:
        
         user@ad.server.com@linux-client.ad.server.com's password:
         Creating home directory for user@ad.server.com.
