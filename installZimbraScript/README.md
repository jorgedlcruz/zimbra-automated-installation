# Automating Zimbra Installer configuration
This Directory is for storing matching versions of the installZimbraScript file which can change from Zimbra Version to version.

Should be named as installZimbraScript-{version}

For Zimbra 8.8.15
installZimbraScript-8.8.15


#### File should look like the below for this prompt with the placeholders for with the desired values.
```
AVDOMAIN="DOMAIN_PLACEHOLDER"
AVUSER="admin@DOMAIN_PLACEHOLDER"
CREATEADMIN="admin@DOMAIN_PLACEHOLDER"
CREATEADMINPASS="PASSWORD_PLACEHOLDER"
CREATEDOMAIN="DOMAIN_PLACEHOLDER"
DOCREATEADMIN="yes"
DOCREATEDOMAIN="yes"
DOTRAINSA="yes"
EXPANDMENU="no"
HOSTNAME="HOSTNAME_PLACEHOLDER"
HTTPPORT="8080"
HTTPPROXY="TRUE"
HTTPPROXYPORT="80"
HTTPSPORT="8443"
HTTPSPROXYPORT="443"
IMAPPORT="7143"
IMAPPROXYPORT="143"
IMAPSSLPORT="7993"
IMAPSSLPROXYPORT="993"
INSTALL_WEBAPPS="service zimlet zimbra zimbraAdmin"
JAVAHOME="/opt/zimbra/common/lib/jvm/java"
LDAPBESSEARCHSET="set"
LDAPHOST="HOSTNAME_PLACEHOLDER"
LDAPPORT="389"
LDAPREPLICATIONTYPE="master"
LDAPSERVERID="2"
MAILBOXDMEMORY="512"
MAILPROXY="TRUE"
MODE="https"
MYSQLMEMORYPERCENT="30"
POPPORT="7110"
POPPROXYPORT="110"
POPSSLPORT="7995"
POPSSLPROXYPORT="995"
PROXYMODE="https"
REMOVE="no"
RUNARCHIVING="no"
RUNAV="yes"
RUNCBPOLICYD="no"
RUNDKIM="yes"
RUNSA="yes"
RUNVMHA="no"
SERVICEWEBAPP="yes"
SMTPDEST="admin@DOMAIN_PLACEHOLDER"
SMTPHOST="HOSTNAME_PLACEHOLDER"
SMTPNOTIFY="yes"
SMTPSOURCE="admin@DOMAIN_PLACEHOLDER"
SNMPNOTIFY="yes"
SNMPTRAPHOST="HOSTNAME_PLACEHOLDER"
SPELLURL="http://HOSTNAME_PLACEHOLDER:7780/aspell.php"
STARTSERVERS="yes"
STRICTSERVERNAMEENABLED="TRUE"
SYSTEMMEMORY="3.8"
TRAINSAHAM="ham.RANDOMHAM_PLACEHOLDER@DOMAIN_PLACEHOLDER"
TRAINSASPAM="spam.RANDOMSPAM_PLACEHOLDER@DOMAIN_PLACEHOLDER"
UIWEBAPPS="yes"
UPGRADE="yes"
USEEPHEMERALSTORE="no"
USEKBSHORTCUTS="TRUE"
USESPELL="yes"
VERSIONUPDATECHECKS="TRUE"
VIRUSQUARANTINE="virus-quarantine.RANDOMVIRUS_PLACEHOLDER@DOMAIN_PLACEHOLDER"
ZIMBRA_REQ_SECURITY="yes"
ldap_bes_searcher_password="PASSWORD_PLACEHOLDER"
ldap_dit_base_dn_config="cn=zimbra"
ldap_nginx_password="PASSWORD_PLACEHOLDER"
mailboxd_directory="/opt/zimbra/mailboxd"
mailboxd_keystore="/opt/zimbra/mailboxd/etc/keystore"
mailboxd_keystore_password="PASSWORD_PLACEHOLDER"
mailboxd_server="jetty"
mailboxd_truststore="/opt/zimbra/common/lib/jvm/java/lib/security/cacerts"
mailboxd_truststore_password="changeit"
postfix_mail_owner="postfix"
postfix_setgid_group="postdrop"
ssl_default_digest="sha256"
zimbraDNSMasterIP="127.0.0.53"
zimbraDNSTCPUpstream="no"
zimbraDNSUseTCP="yes"
zimbraDNSUseUDP="yes"
zimbraDefaultDomainName="DOMAIN_PLACEHOLDER"
zimbraFeatureBriefcasesEnabled="Enabled"
zimbraFeatureTasksEnabled="Enabled"
zimbraIPMode="ipv4"
zimbraMailProxy="TRUE"
zimbraMtaMyNetworks="127.0.0.0/8 [::1]/128 [fe80::]/64 IP_PLACEHOLDER/32"
zimbraPrefTimeZoneId="TIMEZONE_PLACEHOLDER"
zimbraReverseProxyLookupTarget="TRUE"
zimbraVersionCheckInterval="1d"
zimbraVersionCheckNotificationEmail="admin@DOMAIN_PLACEHOLDER"
zimbraVersionCheckNotificationEmailFrom="admin@DOMAIN_PLACEHOLDER"
zimbraVersionCheckSendNotifications="TRUE"
zimbraWebProxy="TRUE"
zimbra_ldap_userdn="uid=zimbra,cn=admins,cn=zimbra"
zimbra_require_interprocess_security="1"
zimbra_server_hostname="HOSTNAME_PLACEHOLDER"
INSTALL_PACKAGES="zimbra-core zimbra-ldap zimbra-logger zimbra-mta zimbra-dnscache zimbra-snmp zimbra-store zimbra-apache zimbra-spell zimbra-memcached zimbra-proxy "
```

# Placeholders to use
RANDOMHAM_PLACEHOLDER for ${RANDOMHAM}
RANDOMSPAM_PLACEHOLDER for ${RANDOMSPAM}
RANDOMVIRUS_PLACEHOLDER for ${RANDOMVIRUS}
HOSTNAME_PLACEHOLDER for ${HOSTNAME}
TIMEZONE_PLACEHOLDER for ${TIMEZONE}
IP_PLACEHOLDER for ${IP}
DOMAIN_PLACEHOLDER for ${DOMAIN}
PASSWORD_PLACEHOLDER for ${PASSWORD}

# The script will run the below on the file to splice in the values selected in the placeholder spots. So the placeholders are case sensitive.
```
sed -i -e "s|RANDOMHAM_PLACEHOLDER|${RANDOMHAM}|g" 
sed -i -e "s|RANDOMSPAM_PLACEHOLDER|${RANDOMSPAM}|g"
sed -i -e "s|RANDOMVIRUS_PLACEHOLDER|${RANDOMVIRUS}|g" 
sed -i -e "s|HOSTNAME_PLACEHOLDER|${HOSTNAME}|g"
sed -i -e "s|TIMEZONE_PLACEHOLDER|${TIMEZONE}|g" 
sed -i -e "s|IP_PLACEHOLDER|${IP}|g"
sed -i -e "s|DOMAIN_PLACEHOLDER|${DOMAIN}|g" 
sed -i -e "s|PASSWORD_PLACEHOLDER|${PASSWORD}|g"
```


If version is missing you can run the installer interactively with the --interactive flag and then select the option to export the configuration values to a file during the interactive installation.
```
zimbraEasyInstall.sh zimbra.io --ip 192.168.211.40 --password Zimbra2017 --interactive
```

You can edit that like the above submit a PR or feed those custom values in via the --zimbrascript flag to the installer from local file path.
```
zimbraEasyInstall.sh zimbra.io --ip 192.168.211.40 --password Zimbra2017 --zimbrascript /some/file/path
```

Example at end of interactive configuration option to save config.
```
*** CONFIGURATION COMPLETE - press 'a' to apply
Select from menu, or press 'a' to apply config (? - help) a
Save configuration data to a file? [Yes] 
Save config in file: [/opt/zimbra/config.23758] 
Saving config in /opt/zimbra/config.23758...done.
```

cat the file out then grep/search for your domain/hostname/IP and/or then use sed to replace.

# Set placeholders
```
config='/opt/zimbra/config.23758';
DOMAIN='yourdomain.tld';
sed -i.bak -e 's|TRAINSAHAM=.*|TRAINSAHAM="ham.RANDOMHAM_PLACEHOLDER@DOMAIN_PLACEHOLDER"|g' ${config}
sed -i.bak -e 's|TRAINSASPAM=.*|TRAINSASPAM="spam.RANDOMSPAM_PLACEHOLDER@DOMAIN_PLACEHOLDER"|g' ${config}
sed -i.bak -e 's|VIRUSQUARANTINE=.*|VIRUSQUARANTINE="virus-quarantine.RANDOMVIRUS_PLACEHOLDER@DOMAIN_PLACEHOLDER"|g' ${config}
sed -i.bak -e "s|$(hostname --fqdn)|HOSTNAME_PLACEHOLDER|g" ${config}
sed -i.bak -e "s|$(date +%Z)|TIMEZONE_PLACEHOLDER|g" ${config}
sed -i.bak -e "s|$(wget -qO- -t1 -T2 ipv4.icanhazip.com)|IP_PLACEHOLDER|g" ${config}
sed -i.bak -e "s|${DOMAIN}|DOMAIN_PLACEHOLDER|g" ${config}
```

Common password lines:
```
ldap_bes_searcher_password="PASSWORD_PLACEHOLDER"
ldap_nginx_password="PASSWORD_PLACEHOLDER"
```

SPECIAL NOTE: This is usually not written by the installer but will need to manually added to the file for automated installation.
```
CREATEADMINPASS="PASSWORD_PLACEHOLDER"
```