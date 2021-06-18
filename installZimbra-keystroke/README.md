# Automating Zimbra Installer keystrokes
This Directory is for storing matching versions of the installZimbra-keystrokes file which can change from Zimbra Version to version.

Should be named as installZimbra-keystrokes-{version}

For Zimbra 8.8.15
installZimbra-keystrokes-8.8.15

#### Example prompt from 8.8.15
```
Do you agree with the terms of the software license agreement? [N]
Use Zimbra's package repository [Y]
Install zimbra-ldap [Y] Y
Install zimbra-logger [Y]
Install zimbra-mta [Y] Y
Install zimbra-dnscache [Y]
Install zimbra-snmp [Y]
Install zimbra-store [Y]
Install zimbra-apache [Y]
Install zimbra-spell [Y]
Install zimbra-memcached [Y]
Install zimbra-proxy [Y]
Install zimbra-drive [Y]
Install zimbra-imapd (BETA - for evaluation only) [N]
Install zimbra-chat [Y]
The system will be modified.  Continue? [N]
```


#### File should look like the below for this prompt with just y/n with the desired values. Note that if there 16 questions/prompts your responses will need to match same number
```
y
y
y
y
y
n
y
y
y
y
y
y
y
n
y
y
```

If version is missing you can run the installer interactively with the --interactive flag and then note the number of prompts and answers.
```
zimbraEasyInstall.sh zimbra.io --ip 192.168.211.40 --password Zimbra2017 --interactive
```

You can submit or note those down and submit a PR or feed those custom values in via the --keystrokes flag to the installer from local file path.
```
zimbraEasyInstall.sh zimbra.io --ip 192.168.211.40 --password Zimbra2017 --keystrokes /some/file/path
```