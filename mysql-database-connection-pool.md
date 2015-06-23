<properties linkid="" urlDisplayName="" pageTitle="如何使用连接池访问MySQL Database on Azure- Azure 微软云" metaKeywords="Azure 云，技术文档，文档与资源，MySQL,数据库，连接池，connection pool, Azure MySQL, MySQL PaaS,Azure MySQL PaaS, Azure MySQL Service, Azure RDS" description="
合理的利用连接池访问MySQL Database on Azure会优化性能。本文介绍如何使用连接池有效地访问MySQL Database on Azure，并给出以JAVA为例的示例代码供参考。" metaCanonical="" services="MySQL" documentationCenter="Services" title="" authors="" solutions="" manager="" editor="" />

<tags ms.service="mysql" ms.date="" wacn.date=""/>
# 如何使用连接池访问MySQL Database on Azure<sup style="color: #a5ce00; font-weight: bold; text-transform: uppercase; font-family: '微软雅黑'; font-size: 20px;" class="wa-previewTag"></sup>



数据库连接是一种有限的资源，合理的利用连接池访问MySQL Database on Azure会优化性能。本文介绍如何使用连接池有效地访问MySQL Database on Azure。

对于数据库连接的管理能够显著影响到整个应用程序的性能。为了使您的程序能够达到性能最优，建议您使用数据库连接池连接MySQL Database on Azure。 
数据库连接池负责建立，管理和分配数据库连接。 当应用程序申请一个数据库连接时，它优先分配一个现有的空闲的数据库连接，而不是重新建立一个。当数据库连接使用完毕后，它会回收该连接以备再次使用，而不是直接关闭该连接。

为了更好地说明，本文提供[以JAVA为例的一段示例代码](http://dummyURL.com)，供参考。

