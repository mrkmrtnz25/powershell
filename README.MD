# Installing ADDS using powershell

### Commands to install ADDS and ADDS forrest with DNS
```
install-windowsfeature ad-domain-services  -IncludeAllSubFeature -IncludeManagementTools
Install-ADDSForest  -DomainName  "mark.ca" -installDns
```