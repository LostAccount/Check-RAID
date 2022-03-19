# Check-RAID

This script was found on [ServerFault.com][1] after having asked about differences between hardware and software RAID Systems. One user, Gordon Davisson, added a nice contribution about silent failures of Apple's software RAIDs on Mac OS X. A bad point raised earlier in the comments.

Here is his answer:

> I'll second SvenW's warning about silent failures; if anything, it's a little too good at surviving a drive failure. I've seen the aftermath of a couple of servers that had one drive drop out of a software mirror for some reason (I suspect not coming ready in time after a reboot); everything works fine off the remaining drive until, several months later, something goes wrong with THAT drive -- and it switches back to the drive that glitched the first time, and the last few months have vanished.
>
> Here's a short shell script I whipped up to fix this. Substitute in your email address, save it as something like /etc/periodic/daily/150.check-raid, make it executable, and it should mail you a warning (at 3:15 the next morning) if the raid ever degrades. To test it (strongly recommended in case of spam blocks, etc), plug in a couple of disposable drives (USB keychain drives, whatever), mirror them, unplug one, leave the other overnight and see if you have a warning in your mailbox in the morning.

  [1]:http://serverfault.com/questions/153956/mac-os-x-server-10-6-software-mirrored-raid-worth-it/154344#154344

## The code

The code was copied from Gordon's answer and few adjustments were made.

## Credits

Credits goes to [Gordon Davisson][2] for the original script.

  [2]:http://serverfault.com/users/6621/gordon-davisson

## Compatibility

Mac OS X 10.6, 10.7: Version v1.0.3
Mac OS X 10.5: Version v1.0.2
Older: unknown

## History

### v1.1 - Minor compatibility update

As of Mac OS X 10.6, `diskutil listRAID` is a deprecated synonym for `diskutil appleRAID list`.

Replaced that command for future use, dropping support for 10.5 systems. (Use v1.0.2 instead)

### v1.0.2 - Minor update

New features:  
 - Added log messages. Test running and error notification.

### v1.0.1 - Minor update

New features:  
 - Added Hostname in mail's subject

### v1.0 - Initial commit from copypasted code

Feature basic check of Apple's software RAID system with mail notification to an admin.
