In this project, I conducted a comprehensive security assessment of the server with the IP address 10.10.89.184. The process involved multiple stages, starting with reconnaissance and culminating in the analysis of file contents.

To begin, I used the Gobuster tool to scan the web server directories, which revealed several files, including .htaccess, .htpasswd, server-status (403 Forbidden), and index.php (200 OK). These findings indicated the presence of a web application. Additionally, I checked the exported NFS resources using the showmount command, which led to the discovery of the /mnt/share directory.

To gain access to the NFS, I created a user named hijack with UID 1003 to match the file owner on the remote server. Although an attempt to mount the shared resource using sudo mount failed due to insufficient sudo privileges, I managed to access /mnt/share. There, I found a file named for_employees.txt, which contained FTP credentials: username ftpuser and password W3stV1rg1n14M0un741nM4m4.

Using these credentials, I successfully connected to the FTP server, where I discovered files such as .bash_logout, .bashrc, .from_admin.txt, .passwords_list.txt, and .profile. I downloaded .from_admin.txt and .passwords_list.txt for further analysis. The .from_admin.txt file contained a message from the administrator recommending the use of passwords from the provided list, as they are not found in standard dictionaries. It also noted that brute-force protection was functioning correctly. The .passwords_list.txt file contained 13 potential passwords.

During the analysis of the passwords_list.txt file, one of the keys proved to be valid. Using this password, I successfully logged into the website, gaining access to the web application. This access allowed me to continue exploring and analyzing the system, as well as to check for potential privilege escalation opportunities or additional vulnerabilities. The successful authentication underscored the importance of testing all possible passwords and highlighted the need for stronger security measures to prevent such attacks.

Personal Reflection:
In this project, I successfully identified and exploited several vulnerabilities in the server's security. By meticulously scanning directories, accessing NFS shares, and analyzing retrieved files, I was able to gain unauthorized access to the web application. This experience has reinforced the critical importance of robust security practices, such as using complex, unique passwords and regularly auditing system access controls. My work on this project has not only enhanced my technical skills but also deepened my understanding of the challenges involved in securing digital assets.
