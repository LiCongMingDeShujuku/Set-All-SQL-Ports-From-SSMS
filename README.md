![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# POST TITLE
#### SECONDARY TITLE
**TIME STAMP**

![#](images/##############?raw=true "#")

## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
有些人认为设置端口的唯一选择是直接从服务器设置。其实你无需逐字登录到SQL Server所在的Windows Server以设置端口。如果你在安装了SQL的Windows Server上具有管理员权限的帐户，则可以照常使用SSMS。

如果你有，只需要运行如下逻辑：

## English
Some people feel the only option for setting the ports is from the server directly. You don’t need to literally logon to the Windows Server where SQL Server resides in order to set the port. You can use SSMS as usual provided you have an account that has admin rights on the Windows Server where SQL is installed.

If you do; simply run this:

---
## Logic
```SQL
use master;
set nocount on
exec sp_configure 'show advanced options', '1'; reconfigure
exec sp_configure 'xp_cmdshell', '1'; reconfigure
go
 
exec master..xp_cmdshell
'@echo SETTING ALL STANDARD SQL PORTS
@echo SQL SERVICE PORTS 1433
netsh advfirewall firewall add rule name="SQL Server" dir=in action=allow protocol=TCP localport=1433 @echo DEDICATED ADMIN PORTS 1434
netsh advfirewall firewall add rule name="SQL Admin Connection" dir=in action=allow protocol=TCP localport=1434 @echo SERVICE BROKER PORTS
netsh advfirewall firewall add rule name="SQL Service Broker" dir=in action=allow protocol=TCP localport=4022 @echo TSQL/RPC port 135
netsh advfirewall firewall add rule name="SQL Debugger/RPC" dir=in action=allow protocol=TCP localport=135 @echo SSAS PORTS
netsh advfirewall firewall add rule name="Analysis Services" dir=in action=allow protocol=TCP localport=2383 @echo Enabling SQL Server Browser Service port 2382
netsh advfirewall firewall add rule name="SQL Browser" dir=in action=allow protocol=TCP localport=2382 @echo SETTING STANDARD APP PORTS IF ANY
@echo HTTP port 80
netsh advfirewall firewall add rule name="HTTP" dir=in action=allow protocol=TCP localport=80 @echo HTTP port 25
netsh advfirewall firewall add rule name="SMTP" dir=in action=allow protocol=TCP localport=25 @echo SSL port 443
netsh advfirewall firewall add rule name="SSL" dir=in action=allow protocol=TCP localport=443 @echo SQL BROWSER PORTS
netsh advfirewall firewall add rule name="SQL Browser" dir=in action=allow protocol=UDP localport=1434 @echo MULTICAST UDP PORTS
netsh firewall set multicastbroadcastresponse ENABLE'


```

希望可以帮到你。(Hope this is useful.)

[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

