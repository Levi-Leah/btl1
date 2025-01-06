# Linux Investigations

## Linux Artifacts: Passwd and Shadow

* `/etc/passwd`
  * used to keep track of every registered user that has access to a system
  * all users will have read access
  * only super users have write access
* `/etc/shadow`
  * contains encrypted passwords as well as information such as account or password expiration values, username, user ID, group ID, home directory, and login shell
  * readable only by the root

## Linux Artifacts: /Var/Lib and /Var/Log

* `/var/lib`
  * on debian-based systems
    * `/var/lib/dpkg/status`
      * includes a list of all installed software packages
* `/var/log`
  * **OS logs**
    * depends on the OS
    * `/var/log/auth.log`
      * contains system authentication information, including user logins
    * `/var/log/dpkg.log`
      * contains information that is logged when a package is installed or removed using the ‘dpkg’ command
    * `/var/log/btmp`
      * contains information about failed login attempts
    * `/var/log/cron`
      * cron daemon logs info here
    * `/var/log/secure`
      * contains information related to authentication and authorization privileges
    * `/var/log/faillog`
      * contains user failed login attempts
  * **Web Server Logs**
    * Linux-based systems are often used to run web server frameworks, such as Apache and Nginx
    * `var/log/apache2/access.log`
      * logs requests made to the web server including:
        * The client IP address making the request
        * The resource they are trying to access
        * The HTTP method, which will most often be GET
          * to get a resource, such as images in a web page
        * The user-agent used by the client IP
          * this should typically be a browser user-agent, such as Chrome, Firefox, etc
        * the timestamp of the request
        * size
      * example: `52.50.100.106 - SBTUser [27/Jul/2020:15:30:00 -0600] "GET /logo.png HTTP/1.1" 200 379`
        * `52.50.100.106` - The IP address of the client making the request to the web server
        * `SBTUser` - The userid of the account making the request
          * if they are logged in and the website is using accounts
        * `[27/Jul/2020:15:30:00 -0600]` - The timestamp of the request
        * `“GET /logo.png HTTP/1.1”` - The resource that is being accessed, in this case the IP is retrieving the logo image file so it can be displayed on a page
        * `200` - The HTTP response code
        * `379` - The size of the file sent to the client

## Linux Artifacts: User Files

* **Bash History**
  * `.bash_history` in user's home dir
  * includes a list of commands that have been run by the specific user
  * `history -c` clears cli history but not the `.bash_history`
* **Hidden files and directories**
  * files starting with `.`
  * always use `ls -a`
* **Clear files and directories**
  * any file accessible through terminal or GUI
  * default user dirs
    * Desktop, Downloads, Music, Pictures, Public, Templates, Videos, Trash
* **Steganography**
  * The practice of concealing messages or information within other non-secret text or data
  * e.g. having a text file that contains secret information, where the text file is actually hidden inside an innocent image file
  * You can also insert hidden messages in the form of text strings within a file’s metadata
  * **example: Hiding ZIP Files Inside Images**
    * get a txt file
    * zip the txt file
    * get an image
    * `cat image.jpg archive.zip > image2.jpg`
    * unzip the image to retreive the message
  * **example: Using Steghide to Hide and Retrieve Files**
    * allows you to password protect the file we’re hiding data inside, known as the cover file
    * `steghide embed -cf image.jpg -ef file.txt`
      * doesn't work on certain filetypes
    * `steghide extract -sf image.jpg`
  * **example: Hiding Strings in Metadata**
    * `exiftool -Comment="Super Sneaky!" image.jpg`
    * `exiftool image.jpg`
      * comment is now part of the metadata

## Linux Artifacts: Memory

* capturing the system's memory can provide a goldmine of information, such as processes that are running, their relationships with other processes, established network connections, and much more
* you can use various tools to create a memory dump, a file containing the contents of the system's memory at the time of acquisition
  * [LiME](https://github.com/504ensicsLabs/LiME) - git repo
  * [memdump](https://manpages.ubuntu.com/manpages/trusty/man1/memdump.1.html) - ubuntu