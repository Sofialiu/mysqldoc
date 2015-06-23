<properties linkid="" urlDisplayName="" pageTitle="如何使用SSL访问MySQL Database on Azure- Azure 微软云" metaKeywords="Azure 云，技术文档，文档与资源，MySQL,数据库，连接池，connection pool, Azure MySQL, MySQL PaaS,Azure MySQL PaaS, Azure MySQL Service, Azure RDS" description="
通过SSL加密访问数据库，可以保障您访问的安全性，本文介绍如何下载并配置SSL证书。目前MySQL Database on Azure支持利用公钥在服务器端进行加密验证。" metaCanonical="" services="MySQL" documentationCenter="Services" title="" authors="" solutions="" manager="" editor="" />

<tags ms.service="mysql" ms.date="" wacn.date=""/>
# SSL安全访问MySQL Database on Azure<sup style="color: #a5ce00; font-weight: bold; text-transform: uppercase; font-family: '微软雅黑'; font-size: 20px;" class="wa-previewTag"></sup>


通过SSL加密访问数据库，可以保障您访问的安全性，本文介绍如何下载并配置SSL证书。目前MySQL Database on Azure支持利用公钥在服务器端进行加密验证。

在您创建MySQL Database on Azure实例时，我们强烈建议您将数据库实例与其他Azure服务放在同一区域，即使不用SSL加密，也可保障安全性。


## 步骤 1:下载服务器端SSL证书
[点击下载](http://dummy.com)SSL证书至本地。

## 步骤 2：配置SSL证书
您可以通过您熟悉的MySQL客户端或语言进行SSL证书的加载配置，本文列举三种常见的配置方法，供您参考。
### 方法一：利用命令行进行配置
打开mysql.exe, 命令行键入 '--ssl-ca= localpath/certname.pem -u username -p -h hostname' 通过SSL加密访问MySQL Database。

![mysql.exe访问数据库][1]

>**提示** SSL状态中出现Cipher in use即证明加密成功。


### 方法二：利用MySQL客户端进行配置
以MySQL Workbench为例，通过Parameters标签设置访问数据库的Connection String，如下图所示。

![配置connection string][2]

通过SSL标签配置SSL证书.

![配置SSL证书][3]

>**注意** 在Use SSL中选择‘If Available’，否则可能会造成配置失败。 在Test Connection过程中可能会提示SSL not enabled，这是一个假预警，点击确认后连接数据库，通信过程已加密。
>
>![errormessage][4]
>

### 方法三：利用函数进行配置
以Python为例，下图是一段示例代码，供参考：

![python SSL访问][5]


<!--Image references-->
[1]: ./img/ssl-001.png
[2]: ./img/ssl-002.png
[3]: ./img/ssl-003.png
[4]: ./img/ssl-004.png
[5]: ./img/ssl-005.png
