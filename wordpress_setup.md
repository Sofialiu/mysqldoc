# 如何使用MySQL Database on Azure来配置WordPress网站



WordPress是一种使用非常广泛的CMS系统。本文介绍如何使用 MySQL Database on Azure 和Azure Web应用来安装配置WordPress。



## 步骤 1:下载最新版WordPress安装包
您可以通过[WordPress官方网站]( https://wordpress.org/download/)下载最新版的安装包到您的本地存储目录。并进行解压到该目录中。

## 步骤 2：新建MySQL Database on Azure的服务器
您可以通过[Windows Azure管理门户](https://manage.windowsazure.cn)创建您的MySQL服务器。
![创建MySQL服务器][1]

> **注意** 将下图中允许的服务设置成“是”以便允许Azure Web应用链接此MySQL服务器。（默认选项是“否”）

![允许的服务][2]


### 新建供WordPress使用的MySQL数据库（必备步骤）
将工作区切至“数据库”，点击屏幕下方“新建”按钮进行数据库的创建。

![新建数据库][3]

> **注意** 用户需在管理门户中手动创建MySQL数据库。如果忽略此步骤，将会造成WordPress部署失败。

## 步骤 3:新建Web应用
详细步骤请参阅 [如何创建和部署Web应用](http://www.windowsazure.cn/manage/services/web-sites/how-to-create-websites/)
![新建Web应用][4]

### 部署WordPress安装文件
接下来，将第一步中解压出来的所有WordPress安装文件部署到刚创建的Web应用中。这里建议使用Git来做部署操作。具体方式请参见[从源控件发布到 Azure 网站](http://www.windowsazure.cn/documentation/articles/web-sites-publish-source-control/)

> **注意** 步骤3 主要针对WordPress的新用户，若您已经使用Azure Web应用并已成功部署WordPress安装文件并开始使用，出于内容一致性的目的，建议您将数据进行导出，重新安装部署WordPress并与新建的MySql数据库成功连接之后，再进行数据导入。具体的Wordpress数据导入导出，请通过WordPress控制台来完成（如下图所示）。
> 
![WordPress导入导出][9]


## 步骤 4:安装配置WordPress


### 1. 访问部署Web应用
访问之前创建的Web应用，进入WordPress配置页面，选择所要使用的语言，屏幕将会出现下图中显示的内容。
![配置WordPress][5] 

### 2. 连接配置MySQL数据库
将第二步所创建数据库的详细配置信息填入下图界面中。

![连接WordPress][6] 

当您看到下图所示，表示您的WordPress与MySQL的连接已经成功了。

![成功连接WordPress][7] 

点击进行安装，完成您的WordPress部署工作。


## 步骤 5:使用WordPress
在完成上述步骤后，访问您之前创建的Web应用，您将看到已经生效的WordPress主界面。现在请开始您的WordPress使用之旅！
![安装WordPress][8] 



<!--Image references-->
[1]: ./img/001.png
[2]: ./img/002.png
[3]: ./img/003.png
[4]: ./img/004.png
[5]: ./img/005.png
[6]: ./img/006.png
[7]: ./img/007.png
[8]: ./img/008.png
[9]: ./img/009.png