<properties linkid="" urlDisplayName="" pageTitle="如何高效连接到MySQL Database on Azure- Azure 微软云" metaKeywords="Azure 云，技术文档，文档与资源，MySQL,数据库，连接池，connection pool, Azure MySQL, MySQL PaaS,Azure MySQL PaaS, Azure MySQL Service, Azure RDS" description="
合理的利用连接池访问MySQL Database on Azure会优化性能。本文介绍如何使用连接池有效地访问MySQL Database on Azure，并给出以JAVA为例的示例代码供参考。" metaCanonical="" services="MySQL" documentationCenter="Services" title="" authors="" solutions="" manager="" editor="" />

<tags ms.service="mysql" ms.date="" wacn.date=""/>
# 如何高效连接到MySQL Database on Azure<sup style="color: #a5ce00; font-weight: bold; text-transform: uppercase; font-family: '微软雅黑'; font-size: 20px;" class="wa-previewTag"></sup>



数据库连接是一种有限的资源，合理的利用连接池访问MySQL Database on Azure会优化性能。本文介绍如何使用连接池或长连接高效效地访问MySQL Database on Azure。

## 通过连接池访问数据库 （推荐）##
对于数据库连接的管理能够显著影响到整个应用程序的性能。为了使您的程序能够达到性能最优，建议您使用数据库连接池(connection pool)或长连接(persistent connection)连接MySQL Database on Azure。 
数据库连接池负责建立，管理和分配数据库连接。 当应用程序申请一个数据库连接时，它优先分配一个现有的空闲的数据库连接，而不是重新建立一个。当数据库连接使用完毕后，它会回收该连接以备再次使用，而不是直接关闭该连接。

为了更好地说明，本文提供[以JAVA为例的一段示例代码](http://wacnstorage.blob.core.chinacloudapi.cn/marketing-resource/documents/MySQLConnectionPool.java )，供参考。

## 通过长连接访问数据库 （推荐）##
PHP中建议您使用长连接，长连接的概念与连接池的概念类似。需要注意的是PHP目前有三种驱动，除Mysqli外，其他两种驱动均支持Persistent Connection. 

查看[利用PDO建立长连接](http://php.net/manual/en/pdo.connections.php)； 
查看[利用MySQL引擎建立长连接](http://php.net/manual/en/function.mysql-pconnect.php)。

## 通过短连接访问数据库##
基于资源的有效性，我们强烈推荐您使用连接池或是长连接访问数据库。但如果您使用短连接，在并发连接数接近上限，连接出现失败的情况下，我们建议您尝试多次连接，可以适当设定等待时间，初次等待时间可以较短，后依次放长。