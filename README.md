1. 启动
```
docker-compose -f docker-compose.yml up
```

2. 连接mysql数据库(数据库密码自行设置，这里用123456&)
```
mysql -hlocalhose -p123456& -P3306
```

2. 从[这里](https://github.com/alibaba/nacos/blob/develop/distribution/conf/nacos-mysql.sql)获取nacos初始数据库，并导入mysql

3. 创建nacos数据库和nacos用户。

```
CREATE DATABASE `nacos` /*!40100 DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci */ /*!80016 DEFAULT ENCRYPTION='N' */
CREATE USER 'nacos'@'%' IDENTIFIED BY 'nacos';
grant all on nacos.* to 'nacos'@'%' with grant option;
flush privileges;
```