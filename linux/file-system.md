#### Directory Structure

* / : Root, the top of the file system hierarchy
* /bin : binaries and executable 
* /etc : system configuration files
  * /passwd: all user profile
* /home : home directory
* /opt : optional and third-party software
* &lt;company name&gt;/&lt;software name&gt;
* /tmp : temp files, cleared at reboot
* /srv : data which is served by the system
* /www: web server files
* /ftp : FTP files
* /sys : Used to display and sometimes configure the devices known to the linux kernel
* Access Level
* root access : system administrator
  * may need for install, start and stop applications
* normal access
* file types
* hidden files \(ls -a , ls- F\) : begins with . 
* link : pointer to an actual file 
* permissions, user group and creation mask
* chmod, groups, chgroup and umask command

#### Install Software

* Packages: a collection of files = data + metadata
  * metadata: package description, version, dependencies
* Package Manager: install, upgrade, and removes packages, manages dependencies, keeping track of installed files
* PRM distro
  * yum search &lt;string&gt;
  * yum info \[package\] 
  * yum install \[-y\] &lt;pacakge&gt;
  * yum remove &lt;package&gt;
  * rpm -qa: list all installed packages
  * rpm -qf &lt;path to file&gt;: listed file's packages
  * rpm -ql package: list package files
  * rpm -ivh package.rpm: install packages
  * rpm -e &lt;package&gt;: remove 
* DEB distro - advanced packaging tool
  * apt-cache search &lt;string&gt;
  * apt-get install \[-y\] &lt;package&gt;
  * apt-get remove package: remove but keep configurations
  * apt-get purge package: remove all
  * apt-cache show &lt;package&gt;: show info
  * dpkg -l: list installed
  * dpkg -S &lt;path&gt;: file's package
  * dpkg -L &lt;package&gt;:list all files in package
  * dpkg -i package.deb: install package

#### File Permission

* chmod &lt;permission&gt; &lt;files&gt; - change permission control \(mod\)
  * **permission**
    * symbolic representation
      * -: regular file, d:directory, l:symbolic link
      * a - all, g -group, o-others, u -user
      * r,w,x - read, write, execute
      * * * add permission, - remove permission, = set permission \(exactly\)
      * eg. chmod a+x &lt;file&gt;
    * octal number representation - rwx 
      * 7 = 111 : all rights
      * 6 = 110 : read and write
      * 5 = 101 L read and execute
      * 4 = 100: read only
      * 0: no permissions
* uamsk \[-S\] \[mode\] : set the file creation mask to mode \( default permission\)
  * permission  = base permission - umask \(eg 777 - 022 = 755\) 
    * common: -007
  * -S: symbolic notation
  * default 777 for directory, 666 for file
  * special modes - add o in the front
    * **setuid, setgid, sticky**

#### Users, Group and Change Users

* groups: display the users group
  * id -Gn: the same
* chgroup : change group
* ln
* * diff
* su \[username\]: change user ID or become super user
  * su \[username\] - : hyphen used to provide an environment that same to user logged in directly
  * su \[username\] -c &lt;command&gt; : execute a command
* sudo \[username\]: execute as another user, typically the root
  * sudo -l: list available commands
  * sudo &lt;command&gt;:run as root
  * sudo -u &lt;user&gt; &lt;command&gt;: run as user \(including the root\)
  * sudo -su: switch to super user
  * sudo su -: switch with environment
  * sudo su -&lt;username&gt;: switch to user
  * sudo \[-u &lt;user&gt;\] -s: start a shell
  * visudo: edit /etc/sudoers file
    * user host=\(users\)\[NOPASSWD:\]commands
* whoami: display current user identity 
* which &lt;command&gt; : locate a command, display the full path of a command \($PATH Controls the search path\)

#### Redirect Input/Output

In Linux, almost everything is a file, including standard I\O

* &lt;commands&gt; \[file descriptor\] &lt;redirection operator&gt; &lt;filename&gt;
* file descriptor
  * stdin : 0
  * stdout: 1
  * stderr: 2
* redirection
  * &gt;:redirects standard output to a file, overwrite
  * &gt;&gt;: redirect, append
  * &lt; redirect from a file
  * &: indicate using descriptor
  * eg. 2&gt;&1: combine output and error, 2&gt;&lt;file&gt;: redirect
* \dev\null: to no where \( the null device\)

#### Get Connected

* telnet&lt;server name&gt; : talk to the server, replaced by the ssh
* ssh \[-i keylocation\] -p &lt;port number&gt; &lt;username@servername&gt;
  * ssh -keygen
  * ~/.ssh file to put in your key
* wget: web-get: download URL files
* wget : web-get download the URL file
* file transfer: 
  * need a client, use pscp.exe/psftp.exe in PuTTy on Windows, graphical client like FileZilla, WinSCP, Cyberduck
  * scp &lt;source&gt; &lt;destination&gt; : SCP- using secure shell protocol\(SSH\): can copy and download
  * sftp&lt;host&gt; : SFTP -start a secure file transfer session
    * lpwd: see local pwd
    * put: upload
  * * quit to quit
  * ftp&lt;host&gt;: not encrypted

### Common Linux Sfotwares

* editors
  * vim, emacs,gvim
  * gedit
  * kedit
  * Kate
* Office
  * LibreOffice
  * Abiword
  * 



