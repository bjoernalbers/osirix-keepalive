# OsiriX-KeepAlive

Restart [OsiriX](https://github.com/pixmeo/osirix) automatically after a crash.


## Install

Download the property list (a.k.a. plist) into the users LaunchAgents
directory and load it:

```
cd ~/Library/LaunchAgents/
curl -L -o com.osirix-viewer.keepalive.plist https://raw.github.com/bjoernalbers/osirix-keepalive/com.osirix-viewer.keepalive.plist
launchctl load -w com.osirix-viewer.keepalive.plist
```

OsiriX will then start and also when the user logs in.


## Usage

*Forcefully* quit OsiriX or simply run `killall OsiriX` to make it raise
from the dead.
Of course a crash should also work ;-)

**NOTE: OsiriX will (intentionally) not start again when you just quit
it because this wouldn't be a crash!
If this has happened: Log in again or unload and load the plist.**

PS: You can find out when OsiriX crashed by searching the syslog via
`bzgrep com.osirix-viewer.keepalive /var/log/system.log*`:

```
Oct 10 14:42:24 ghost com.apple.launchd.peruser.501[261] (com.osirix-viewer.keepalive[84244]): Exited: Terminated: 15
Oct 10 15:55:47 ghost com.apple.launchd.peruser.501[261] (com.osirix-viewer.keepalive[84447]): Exited: Terminated: 15
```


## Uninstall

Unload the plist and delete it:

```
cd ~/Library/LaunchAgents/
launchctl unload -w com.osirix-viewer.keepalive.plist
rm com.osirix-viewer.keepalive.plist 
```


## Copyright

Copyright (c) 2013 Björn Albers
