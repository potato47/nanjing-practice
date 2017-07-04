# Day6

 **[HOME](../README.md)**

## 添加属性到Action属性栈

```java
ActionContext.getContext().getValueStack().push(Object o);//o的所有的属性都可以直接访问
```

```java
ActionContext.getContext().getValueStack().set(String s, Object o);//可以通过s.value访问
```



## 关联表数据不显示

1.在hbm.xml加lazy=“false"

```xml 
<many-to-one name="department" class="com.next.pojo.Department" fetch="select" lazy="false">
	<column name="department" />
</many-to-one>
```
2.在web.xml加

```xml
<filter>
	<filter-name>OpenSessionInViewFilter</filter-name>
  	<filter-class>org.springframework.orm.hibernate3.support.OpenSessionInViewFilter</filter-class>
  	<init-param>   
         <param-name>flushMode</param-name>   
         <param-value>AUTO</param-value>   
    </init-param>
  	</filter>
  	<filter-mapping>
  		<filter-name>OpenSessionInViewFilter</filter-name>
  		<url-pattern>/*</url-pattern>
</filter-mapping>
```

## 级联删除

```xml
<set name="employees" inverse="true" cascade="delete">
	<key>
		<column name="department" />
	</key>
	<one-to-many class="com.next.pojo.Employee" />
</set>
```
## 更新删除数据无效

推测跟spring事务有关

flush清空缓存

```java
getHibernateTemplate().delete(persistentInstance);
getHibernateTemplate().flush();
```