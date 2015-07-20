<properties linkid="" urlDisplayName="" pageTitle="MySQL FAQ - Azure 微软云" metaKeywords="Azure 云，技术文档，文档与资源，MySQL,数据库，常见问题，FAQ" description="针对用户在使用MySQL Database on Azure中遇到的一些常见技术问题，提供快速解答。如果您仍存有疑问，欢迎联系技术支持。" metaCanonical="" services="MySQL" documentationCenter="Services" title="" authors="" solutions="" manager="" editor="" />

<tags ms.service="mysql" ms.date="" wacn.date=""/>

#技术FAQ





	
	为了保证连接可以高效的得到充分利用，我们建议您使用连接池(connection pool)或是长连接(persistent connection)连接数据库。查看[如何高效连接到MySQL Database on Azure](/documentation/articles/mysql-database-connection-pool/);

- MYSQL Database on Azure 是否支持用户通过命令行设置权限？
	
	可以支持，目前我们的服务支持用户通过[管理门户](https://manage.windowsazure.cn/)创建用户，之后可利用“grant”命令进行权限分配。