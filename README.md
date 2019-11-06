# apidoc

###使用方法
1. 创建数据库：apidoc（字符集utf8mb4或utf8），导入脚本：api-web/db/sosoapi-1.0.0.sql
2. 修改配置
api-web/src/main/filters/filter-dev-master.properties
api-web/src/main/resources/mail-cfg.properties
3. 构建项目：mvn install，mvn compile resources:resources war:exploded -f api-web/pom.xml
4. 部署到tomcat：&lt;Context docBase="H:\works\itecheast\apidoc\api-web\target\apidoc" path="/apidoc"/&gt;
5. 访问：http://localhost:8080/apidoc/，登录：admin@qq.com，密码：123456

###常见问题
1. 数据库字符串：mysql高版本支持utf8mb4则优先使用，低版本使用utf8也行。

spring-mybatis.xml，连接池使用了druid，因为原来的bonecp在低版本mysql时报错。

2. 发送邮件失败：

java.lang.NoSuchMethodError: com.sun.mail.util.TraceInputStream，org.apache.commons.mail.EmailException: Sending the email to the following server failed。解决办法：base-mail/pom.xml，修改commons-email为1.5版本。
