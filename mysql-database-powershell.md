<properties linkid="" urlDisplayName="" pageTitle="使用PowerShell管理MySQL Database on Azure - Azure 微软云" metaKeywords="Azure 云,技术文档,文档与资源,MySQL,数据库,入门指南,Azure MySQL, MySQL PaaS,Azure MySQL PaaS, Azure MySQL Service, Azure RDS" description="帮助您迅速掌握如何使用Azure PowerShell来管理MySQL Database on Azure服务。" metaCanonical="" services="MySQL" documentationCenter="Services" title="" authors="sofia" solutions="" manager="" editor="" />  

<tags ms.service="mysql" ms.date="" wacn.date="10/14/2015"/>

#使用PowerShell管理MySQL Database on Azure
MySQL Database on Azure支持您通过PowerShell脚本创建管理删除MySQL服务器、数据库、防火墙原则、用户等，同时支持您通过脚本更改参数设置。本文主要介绍如何使用PowerShell脚本快速创建使用MySQL服务，并简单介绍如何利用脚本删除以及更改MySQL Database on Azure的配置操作。

##安装Azure PowerShell
运行脚本前，您需要安装并运行Azure PowerShell。您可以通过[运行Microsft Web平台安装程序](http://go.microsoft.com/fwlink/p/?linkid=320376&clcid=0x409)下载并安装最新版本Azure PowerShell 。可参阅[如何安装和配置Azure PowerShell](http://www.windowsazure.cn/documentation/articles/powershell-install-configure)来了解更多详细步骤。
用于创建和管理MySQL Database on Azure 数据库的cmdlet位于Azure资源管理器模块中。启动Azure PowerShell时，默认情况下将导入Azure模块中的cmdlet。若要切换到Azure资源管理器模块，请使用以下命令转换：

```
Switch-AzureMode -Name AzureResourceManager
```

如果收到警告"Switch-AzureMode cmdlet已过时，将在以后的版本中删除"，可以忽略该消息并转到下一部分。此命令将在新版本淘汰，因此建议您更新Azure PowerShell到最新版。有关详细信息，请参阅[将Windows PowerShell与资源管理器配合使用](http://www.windowsazure.cn/documentation/articles/powershell-azure-resource-manager)

##配置账户信息
在针对Azure订阅运行PowerShell之前，必须先将Azure账户绑定。运行以下命令，在登陆页面输入与Azure管理门户相同的电子邮件和密码，进行身份验证。

```
Add-AzureAccount -Environment AzureChinaCloud 
```

若您有多个SubID需要选择，可通过运行 Select-AzureSubscription命令进行选择。

##订阅MySQL Database on Azure服务
运行以下命令订阅MySQL服务。

```
Register-AzureProvider -ProviderNamespace "Microsoft.MySql"
```

#快速入门创建使用MySQL数据库服务

##创建资源组
如果您已有资源组，可以直接创建服务器，或者编辑运行以下命令，创建新的资源组：

```
New-AzureResourceGroup -Name "resourcegroupChinaEast" -Location "China East"
```

>[AZURE.NOTE] ** 注意:Location的默认选项为China North, 处于安全性考虑，强烈建议您将资源组中的服务选择在同一个地域中。**

##创建服务器
编辑运行以下命令，定义您的服务器名称、位置、版本等信息来完成服务器创建。

```
New-AzureResource -ResourceType "Microsoft.MySql/servers" -ResourceName testPSH -ApiVersion 2015-09-01 -ResourceGroupName resourcegroupChinaEast -Location chinaeast -PropertyObject @{version = '5.5'}
```

>[AZURE.NOTE] ** 注意:“-ApiVersion 2015-09-01”指定了API的版本，是必要的。另外，运行上述命令可以完成MySQL服务器的创建，但没有用户，须在后续步骤中创建用户设置权限，这一点和使用Azure管理门户创建稍有不同**

##创建服务器防火墙原则
编辑运行以下命令，定义您的防火墙原则名称、IP白名单范围（起始IP地址，终止IP地址）等信息来完成防火墙原则的创建。

```
New-AzureResource -ResourceType "Microsoft.MySql/servers/firewallRules" -ResourceName testPSH/rule1 -ApiVersion 2015-09-01 -PropertyObject @{startIpAddress="0.0.0.0"; endIpAddress="255.255.255.255"} -ResourceGroupName resourcegroupChinaEast
```

##创建数据库
编辑运行以下命令，定义您的数据库名称、字符集等信息完成数据库创建。

```
New-AzureResource -ResourceType "Microsoft.MySql/servers/databases" -ResourceName testPSH/demodb -ApiVersion 2015-09-01 -ResourceGroupName resourcegroupChinaEast -PropertyObject @{collation='utf8_general_ci'; charset='utf8'}
```

##创建用户
编辑运行以下命令，定义您的用户名、密码等信息完成数据库创建。

```
New-AzureResource -ResourceType "Microsoft.MySql/servers/users" -ResourceName testPSH/admin -ApiVersion 2015-09-01 -ResourceGroupName resourcegroupChinaEast -PropertyObject @{password='abc123'}
```

##添加用户权限
编辑运行以下命令，设置数据库读写权限给用户。权限分为"Read"以及"ReadWrite"。

```
New-AzureResource -ResourceType "Microsoft.MySql/servers/databases/privileges" -ResourceName testPSH/demodb/admin -ApiVersion 2015-09-01 -ResourceGroupName resourcegroupChinaEast -PropertyObject @{level='ReadWrite'}
```


#其他创建、删除、修改操作
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

#资源类型以及参数列表
其他未列出的操作，您可以通过下载[MySQL资源类型参数信息](http://wacnppe.blob.core.chinacloudapi.cn/marketing-resource/2015-09-01.json )来了解更多。



