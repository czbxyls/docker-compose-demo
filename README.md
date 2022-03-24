1. 启动，这时候nacos会报错，忽略值
```
docker-compose -f docker-compose.yml up
```

2. 连接mysql数据库(数据库密码自行设置，这里用123456&)
```
mysql -hlocalhost -p"123456&" -P3306
```

3. 创建nacos数据库和nacos用户。

```
CREATE DATABASE `nacos`; /*!40100 DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci */ /*!80016 DEFAULT ENCRYPTION='N' */
CREATE USER 'nacos'@'%' IDENTIFIED BY 'nacos';
grant all on nacos.* to 'nacos'@'%' with grant option;
flush privileges;
```

4. 从[这里](https://github.com/alibaba/nacos/blob/develop/distribution/conf/nacos-mysql.sql)获取nacos初始数据库，并导入nacos库

5. 重启服务
docker-compose -f docker-compose.yml down & docker-compose -f docker-compose.yml up
6. 访问： http://localhost:8848/nacos