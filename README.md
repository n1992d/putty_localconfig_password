putty_localconfig_password
==========================

putty with localconfigfile and auto input  password based on 0.063

storing configuration into file is by http://jakub.kotrla.net/putty/

This PuTTY stores its configuration (sessions, ssh host keys, random seed file path) to file instead of registry. Every session and ssh host key is stored in a separate file. Default paths are (where . represents executable directory):

./sessions/packedSessionName
./sshhostkeys/packedHostName
./putty.rnd
Path for saving configuration can be set via file putty.conf. Current working directory is searched first, if putty.conf is not found there, executable directory (same directory as putty/pscp/psftp/plink/pageant.exe) is searched. putty.conf should look like this (if it's not found defaults are used):

		;comment line
		sessions=%SYSTEMROOT%\ses
		sshhostkeys=\ssh\hostkeys
		seedfile=C:\putty.rnd
		sessionsuffix=.session
		keysuffix=.hostkey
		jumplist=jumplist.txt
	
You can use enviroment variables in config (like %SYSTEMROOT%) - string will be expanded via ExpandEnviromentString WinAPI function (user-specific variables are not supported yet).

sessionsuffix and keysuffix are optional, defaults are empty. If set, every file has a suffix as defined (saved sessions via sessionsuffix and ssh host keys via keysuffix). Primary purpose is to avoid "*.com" files from names like ssh.domain.com. Both are limited to 15 characters. 
Warning: if you already have saved some sessions or ssh host keys and you change these suffixes, you have to manually rename (append them to) all files.

Jumplist is new feature in Windows 7 supported by PuTTY 0.61. Because this PuTTY should be lightweight, if you do not set path to jumplist, none will be created.

This PuTTY is still able to load configuration from registry. Sessions loaded from registry are marked [registry]. When PuTTY is checking ssh host key and it's not found in file but in registry, you can move/copy key to file (or of course do nothing).

Pageant loads list of saved sessions from path set in putty.conf, defaults is ./sessions/packedSessionName - it works the same way as PuTTY (including keysuffix setting).

compiled exe download  http://pan.baidu.com/s/1Du02X

