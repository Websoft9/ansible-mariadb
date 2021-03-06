# 更新升级

网站技术日新月异，**更新升级**是维护工作之一，长时间不升级的程序，就如长时间不维护的建筑物一样，会加速老化、功能逐渐缺失直至无法使用。  

这里注意更新与升级这两词的差异（[延伸阅读](https://support.websoft9.com/docs/faq/zh/tech-upgrade.html#更新-vs-升级)），例如：  

- 操作系统打个补丁常称之为**更新**，Ubuntu16.04 变更为 Ubuntu18.04，称之为**升级**
- MariaDB5.6.25-->MariaDB5.6.30 常称之为**更新**，MariaDB5.6->MariaDB5.7 称之为**升级**

MariaDB 完整的更新升级包括：系统级更新（操作系统和运行环境）和 MariaDB 程序升级两种类型

## 系统级更新

运行一条更新命令，即可完成系统级更新：

``` shell
#For Ubuntu&Debian
apt update && apt upgrade -y

#For Centos&Redhat
yum update -y
```
> 本部署包已预配置一个用于自动更新的计划任务。如果希望去掉自动更新，请删除对应的Cron

## MariaDB 更新升级

### On Linux

上面的系统升级命令，支持小版本升级。例如：5.6.x to 5.6.y 或 5.7.x to 5.7.y

数据库大版本之间的差异较大，无法提供稳妥的升级方案

### On Windows

MariaDB upgrade on Windows Server divided into two parts

1. Use Windows Update to upgrade Windows System
2. Dowload the lastest MariaDB, stop the MariaDB Services and replace the old files of MariaDB

## 常见问题

#### 大版本升级后，无法更改数据库密码？
```
mysql_upgrade -u root -p 13456
```