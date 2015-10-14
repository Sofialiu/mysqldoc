<properties linkid="" urlDisplayName="" pageTitle="使用PowerShell管理MySQL Database on Azure - Azure 微软云" metaKeywords="Azure 云,技术文档,文档与资源,MySQL,数据库,入门指南,Azure MySQL, MySQL PaaS,Azure MySQL PaaS, Azure MySQL Service, Azure RDS" description="本文介绍如何通过PowerShell实现更多MySQL Database on Azure的查询、创建、修改、删除等操作。" metaCanonical="" services="MySQL" documentationCenter="Services" title="" authors="sofia" solutions="" manager="" editor="" />  

<tags ms.service="mysql" ms.date="" wacn.date="10/14/2015"/>

#使用PowerShell管理MySQL Database on Azure
本文主要介绍如何通过PowerShell实现更多MySQL Database on Azure的创建、查看、删除、更改等操作。建议您先阅读[利用Azure 资源管理器与 PowerShell 来部署使用MySQL Database on Azure](/documentation/articles/mysql-database-commandlines)您可以查看[使用PowerShell管理MySQL Database on Azure](/documentation/articles/mysql-database-commandlines)。
[利用Azure 资源管理器与 PowerShell 来部署使用MySQL Database on Azure]一文中介绍了如何端到端利用PowerShell来快速创建MySQL Database on Azure数据服务。
通过上述操作，您已经完成了服务器、数据库、用户、防火墙原则等的创建工作，可以开始使用MySQL Database on Azure的数据库服务。通过Azure PowerShell脚本您可以用New, Remove, Set命令针对MySQL六种资源类型servers, databases, users, privileges, firewallRules，backups）进行创建、删除、更改等操作。上文主要介绍了创建操作如何通过脚本实现，下面将介绍如何用脚本Remove指令删除服务器、数据库等以及如何用Set指令修改参数等数据库管理操作。
通过Remove指令可以进行对以下六种资源类型（servers, databases, users, privileges, firewallRules，backups）进行删除操作。以删除数据库为例：
##删除数据库
编辑运行以下命令，指定您的数据库名进行删除。

```
Remove-AzureResource -ResourceType "Microsoft.MySql/servers/databases" -ResourceName testPSH/demodb -ApiVersion 2015-09-01 -ResourceGroupName resourcegroupChinaEast
```
通过Set指令可以进行对以下六种资源类型（servers, databases, users, privileges, firewallRules，backups）的属性进行修改操作。以修改MySQL 服务器的wait_timeout参数值为例：
##修改服务器默认参数值
编辑运行以下命令，更改wait_timeout默认值。

```
Set-AzureResource -ResourceType "Microsoft.MySql/servers" -ResourceName testPSH -ApiVersion 2015-09-01 -ResourceGroupName resourcegroupChinaEast -PropertyObject @{options=@{wait_timeout=70}} -UsePatchSemantics
```
通过Get指令可以查看当前MySQL服务器、数据库、用户、备份等列表
##查看服务器列表
编辑运行以下命令，查看当前所有服务器列表
```
Get-AzureResource -ResourceType "Microsoft.MySql/servers"  -ApiVersion 2015-01-01 
```
>[AZURE.NOTE] ** 注意:与其他指令不同，查看服务器中的“-ApiVersion 2015-01-01”，指向ARM的API，其他指令中，均为“-ApiVersion 2015-09-01”，指向MySQL的API。**

##查看数据库列表
编辑运行以下命令，查看当前数据库列表
```
 Get-AzureResource -ResourceType "Microsoft.MySql/servers/databases" -Name testPSH -ApiVersion 2015-09-01 -ResourceGroupName resourcegroupChinaEast
```

#资源类型以及参数列表
其他未列出的操作，您可以通过下载[MySQL资源类型参数信息](http://wacnppe.blob.core.chinacloudapi.cn/marketing-resource/2015-09-01.json )来了解更多。

