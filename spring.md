# IOC
1. `org.springframework.beans`, `org.springframework.context` are the basis
2. `BeanFactory` provides an advanced configuration mechanism capable of managing any type of object.  
`ApplicationContext` is a sub-interface of BeanFactory.
3. `BeanFactory` contains:  
    Easier integration with Spring's AOP features  
    Message resource handling  
    Event publication  
    Application-layer specific context, eg: `WebApplicationContext`
4. `BeanFactory` provides the configuration framework and basic funtionality, `ApplicationContext` adds more enterprise-specific functionality.
5. **bean**: the objects that form the backbone of your application and that are managed by the Spring IoC container. It's an object that is instantiated, assembled, and otherwise managed by a Spring IoC container. It's a simple one of many objects in your application.
6. The `org.springframework.context.ApplicationContext` interface represents the Spring IoC container and is responsible for instantiating, configuring, and assembling the beans.
7. The configuration metadata: XML, Java annotations. Java code
8. In stand-alone applications, it's common to create an instance of `ClassPathXmlApplicationContext` or `FileSystemXmlApplicationContext`
9. In most application scenarios, explicit user code is not required to instantiate one or more instances of a Spring IoC container.
10. XML  
```
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="..." class="...">   
        <!-- collaborators and configuration for this bean go here -->
    </bean>

    <bean id="..." class="...">
        <!-- collaborators and configuration for this bean go here -->
    </bean>

    <!-- more bean definitions go here -->

</beans>
```  
`id` `string` identifies the indicidual bean definition  
`class` defines the type of the bean and uses the fully qualified classname  
(**Dependencies*) 
11. Java
```
    @Configuration
        @Bean
```
12. container loads configuration metadata  
`ApplicationContext context = new ClassPathXmlApplicationContext("services.xml", "daos.xml")`
13. Each individual XML configuration file represents a logical layer or module
14. Use the application context constructor to load bean definitions from all these XML fragments. eg:  
```
<beans>
    <import resource="services.xml"/>
    <import resource="resources/messageSource.xml"/>
    <import resource="/resources/themeSource.xml"/>

    <bean id="bean1" class="..."/>
    <bean id="bean2" class="..."/>
</beans>
```
15. 