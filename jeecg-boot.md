# redis设置  
### 启动服务器`src/redis-server`  
### 启动cli`src/redis-cli`
1. 配置文件redis.conf里设置密码`requirepass`字段(需重启);  
2. 进入redis命令行`src/redis-cli`,设置密码`config set requirepass 密码`,查询密码`config get requirepass`,密码验证`auth 密码`(重启redis后,密码失效) 
#  jeecg-boot 
## 数据库
创建数据库必须有
1. `create_by` 
2. `create_time` 
3. `update_by` 
4. `update_time`字段  
## jeecg-boot配置 
1. `jeecg_datebase.properties`url中`localhost`后为db的名字,与`database_name`一致  
2. `JeecgCodeGenerator.java`中`setTableName`与数据库中表名要一致,`setEntityName`中将表名各首字母大写  


