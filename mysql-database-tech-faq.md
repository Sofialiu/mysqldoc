<properties linkid="" urlDisplayName="" pageTitle="MySQL FAQ - Azure 微软云" metaKeywords="Azure 云，技术文档，文档与资源，MySQL,数据库，常见问题，FAQ" description="针对用户在使用MySQL Database on Azure中遇到的一些常见技术问题，提供快速解答。如果您仍存有疑问，欢迎联系技术支持。" metaCanonical="" services="MySQL" documentationCenter="Services" title="" authors="" solutions="" manager="" editor="" />

<tags ms.service="mysql" ms.date="" wacn.date=""/>

#技术FAQ
- 公共预览版是否有SLA的保证？
	与Azure其他服务一样，根据[世纪互联有关 Azure 的在线服务标准协议](/support/legal/subscription-agreement)，MySQL Database on Azure在公共预览阶段暂不提供SLA保证。尽管如此，MySQL Database on Azure公共预览版的设计实现和运维都是严格以99.9%的高可用性为标准。 - 数据备份占用存储限额吗？
	数据备份不会占用您存储限额。- 一个服务器是否限制数据库的数量？
	在一个MySQL服务器中，用户可创建多个数据库，数量上没有限制，但是多个数据库会共享服务器资源，如数据库数量较多，性能需求较高，建议创建多个MySQL服务器。 - MySQL Database on Azure目前有哪些限制？
	了解更多[MySQL Database on Azure服务限制](/documentation/articles/mysql-database-operation-limitation/)- MySQL Database on Azure 并发连接量不够用？
	
	为了保证连接可以高效的得到充分利用，我们建议您使用连接池(connection pool)或是长连接(persistent connection)连接数据库。查看[如何高效连接到MySQL Database on Azure](/documentation/articles/mysql-database-connection-pool/);

- MYSQL Database on Azure 是否支持用户通过命令行设置权限？
	
	可以支持，目前我们的服务支持用户通过[管理门户](https://manage.windowsazure.cn/)创建用户，之后可利用“grant”命令进行权限分配。