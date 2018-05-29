## Q1 - 想看mapper中SQL解析
```


org.apache.ibatis.builder.xml.XMLConfigBuilder#XMLConfigBuilder(org.apache.ibatis.parsing.XPathParser, java.lang.String, java.util.Properties)
{
    super(new Configuration());
    ErrorContext.instance().resource("SQL Mapper Configuration");
    this.configuration.setVariables(props);
    this.parsed = false;
    this.environment = environment;
    this.parser = parser;
}


配置文件的解析,解析并往configuration中set数据
org.apache.ibatis.builder.xml.XMLConfigBuilder#parse

解析配置
org.apache.ibatis.builder.xml.XMLConfigBuilder#parseConfiguration

解析mapper
org.apache.ibatis.builder.xml.XMLConfigBuilder#mapperElement

解析语句(select|insert|update|delete)
org.apache.ibatis.builder.xml.XMLStatementBuilder#parseStatementNode
{
...
//获取命令类型(select|insert|update|delete)
String nodeName = context.getNode().getNodeName();
...
// 脚本语言,mybatis3.2的新功能 默认为org.apache.ibatis.scripting.xmltags.XMLLanguageDriver
SqlSource sqlSource = langDriver.createSqlSource(configuration, context, parameterTypeClass);
...

...
}





```
