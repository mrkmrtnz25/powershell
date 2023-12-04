# Useful powershell commands for ADDS

### Commands to install ADDS and ADDS forrest with DNS
```
install-windowsfeature ad-domain-services  -IncludeAllSubFeature -IncludeManagementTools4
```
```
Install-ADDSForest  -DomainName  "mark.ca" -installDns
```

### To add IP address and DNS:

#### Show commands
```
Get-NetAdapter
Get-NetIPAddress
```
#### Adding ip address
```
New-NetIPaddress -interfacealias "adapter name" -Ipaddress 192.168 -Prefixlenght 24
```
#### Show commands of DNS settings
```
Get-DnsClientServerAdress
```
#### Adding DNS client ip address
```
Set-DNSClientServerAddress "Interfacealias" -ServerAddress ("Prepared-Dns-address","Alternate DNS"
```
#### To create organization unit
```
New-ADorganizationalUnit -name "Name you want" -protectFromAccidentalDeletion $false or $true
```
#### To remove organization unit
```
remove-ADorganizationalUnit -identity "OU=name of org,DC=,DC=" -Recursive
```
#### To filter organizational unit
```
Get-ADorganizationalUnit -filter 'name -like "name of the orga"'
```
#### To show all ogranizational unit
```
Get-ADorganizationalUnit -filter 'name -like "*"'
```
### To add user to org
```
New-Aduser -name "name of account" -GivenName "name of account" -SurName "surname of account" -SamAccountName "name of account" -UserPrincipalName "name.mark.ca" -Displayname "What name you want to apear" -Path "Ou=centennial,DC=,DC=" -Account password (read-host -assecurestring "input password of account") -passwordneverexpire $true or $ false -enable $true or $false
```
### To show the user 
```
Get-Aduser -filter -Searchbase "ou=centennial,dc=,dc"
```
### To add new group
```
New-Adgroup -name "name of the group" -path "ou=centennial,DC=,DC=" -GroupCategory security -Groupscope Global
```
### To show the group
```
Get-adgroup -filter -searchbase "ou=centennial,DC=,DC="
```
### To add user to the group
```
Add-ADgroupmember -identity "group name" -members _____,_____,_____ <-- multiple user
```
### To show who is in the group
```
get-adgroupmember -identity "name of the group"
```
### To create a file via cmd
```
mkdir nameOfTheFile
```
### To do a smb file
```
new-smbshare -name "name of the file" -path "c: " -fullaccess "name of the user"
```
### Another way to grant access
```
grant-smbshareaccess -name ____ <-name of file  -Accountname _____ <-name of account -accessrights _____ <-what kind of access rights you wan to grant
```
### To show the user accessrights
```
Get-smbshare access -name ____ <- name of the file
```
