### 注解驱动IOC容器【掌握】

xml对应的IOC容器，ClassPathXmlApplicationContext，是在类路径下的xml驱动。

而对于注解配置的取得，应当是Annotation开头的，这就是AnnotationConfigApplicationContext



####  注解驱动IOC的依赖查找

##### 配置类的编写与Bean的注册

相较于xml文件的驱动方式，注解需要的是配置类。

可以将一个配置类比作是一个xml。

配置类没有特殊的限制，只需要在类上标注一个@Configuration即可

```java
@Configuration
public class QuickstartConfiguration {   
}
```

相较于xml的<bean>标签，配置类则使用@Bean

```java
@Configuration
public class QuickstartConfiguration {

    @Bean
    public Person Person() {
        return new Person();
    }

}
```

这种使用方式，可以解释为：**向 IOC 容器注册一个类型为 Person ，id 为 person 的 Bean** 。**方法的返回值代表注册的类型，方法名代表 Bean 的 id** 。当然，也可以直接在 `@Bean` 注解上显式的声明 Bean 的 id ，只不过在注解驱动的范畴里，它不叫 id 而是叫 **name** ：

````java
//    @Bean(value="aaa")
    @Bean(name = "aaa") // 4.3.3之后可以直接写value
    public Person Person() {
        return new Person();
    }
````

这样就算把配置类编写好了。

#####  启动类初始化注解IOC容器

像上面所说的，咱使用 `AnnotationConfigApplicationContext` 来驱动注解 IOC 容器，在构造方法中把配置类传入：

````java
public class AnnotationConfigApplication {
    public static void main(String[] args) throws Exception {
        ApplicationContext ctx
                = new AnnotationConfigApplicationContext(QuickstartConfiguration.class);
        Person person = ctx.getBean(Person.class);
        System.out.println(person);
    }
}
````

#####  注解驱动IOC的依赖注入

编码方式的依赖注入可以说是相当简单了，直接在创建对象后先别着急返回，把里面的值都 set 进去，再返回即可：

````java
    @Bean(name = "aaa") // 4.3.3之后可以直接写value
    public Person Person() {
        Person person = new Person();
        person.setName("person");
        person.setAge(123);
        return person;
    }
````

就相当于：



````java
<bean id="person" class="com.linkedbear.spring.basic_di.a_quickstart_set.bean.Person">
    <property name="name" value="test-person-byset"/>
    <property name="age" value="18"/>
</bean>
````

````java
@Bean
public Cat cat() {
    Cat cat = new Cat();
    cat.setName("test-cat-anno");
    // 直接拿上面的person()方法作为返回值即可，相当于ref,构造注入
    cat.setMaster(person());
    return cat;
}
````

就相当于：

````java
<bean id="cat" class="com.linkedbear.spring.basic_di.a_quickstart_set.bean.Cat">
    <property name="name" value="test-cat"/>
    <property name="master" ref="person"/>
</bean>
````

#### 注解IOC容器的其他用法

翻看 `AnnotationConfigApplicationContext` 的构造方法，可以发现它还有一个方法，是传入一组 `basePackage` ，翻译过来是 “根包” 的意思，它又是什么意思呢？这就涉及到下面的概念了：**组件注册与扫描**。

##### 组件注册与组件扫描【掌握】

上面声明的方式，如果需要注册的组件特别多，那编写这些 `@Bean` 无疑是超多工作量，于是 SpringFramework 中给咱整了几个注解出来，可以帮咱快速注册需要的组件，这些注解被成为**模式注解 ( stereotype annotation )**。

##### 一切组件注册的根源：@Component

在类上标注 `@Component` 注解，即代表该类会被注册到 IOC 容器中作为一个 Bean 。

````java
@Component
public class Person {
    
}
````

相当于 xml 中的：

````java
<bean class="com.linkedbear.spring.basic_dl.a_quickstart_byname.bean.Person"/>
````

如果想指定 Bean 的名称，可以直接在 `@Component` 中声明 **value** 属性即可：

````java
@Component("aaa")
public class Person { }
````

如果不指定 Bean 的名称，它的默认规则是 **“类名的首字母小写”**（例如 `Person` 的默认名称是 `person` ，`DepartmentServiceImpl` 的默认名称是 `departmentServiceImpl` ）。

##### 组件扫描

只声明了组件，咱在写配置类时如果还是只写 `@Configuration` 注解，随后启动 IOC 容器，那它是感知不到有 `@Component` 存在的，一定会报 `NoSuchBeanDefinitionException` 。

为了解决这个问题，咱需要引入一个新的注解：`@ComponentScan` 。

#####  @ComponentScan

在配置类上额外标注一个 `@ComponentScan` ，并指定要扫描的路径，它就可以**扫描指定路径包及子包下的所有 `@Component` 组件**：

````java
@Configuration
@ComponentScan("org.example.annoConfiguration")
public class QuickstartConfiguration {}
````

不指定路径, `@ComponentScan`会扫描本类所在的包 

古老的版本有这样的写法

````java
@ComponentScan(basePackages = "com.linkedbear.spring.annotation.c_scan.bean")
````

这两个属性实质上是一样的，写哪个都可以。

另外注意 `basePackages` 是复数，它可以声明多个扫描包。

声明上 `@ComponentScan` 之后，重新启动配置类，可以发现 `Person` 已经成功被注册。

##### 不使用@ComponentScan的组件扫描

其实，如果不写 `@ComponentScan` ，也是可以做到组件扫描的。在 `AnnotationConfigApplicationContext` 的构造方法中有一个类型为 String 可变参数的构造方法：

<img src="http://39.99.49.158/images/20230424/df29f1a67174.png" alt="image-20230424144238982" style="zoom:33%;" />

<img src="http://39.99.49.158/images/20230424/f07b7ea450f2.png" alt="image-20230424144302300" style="zoom:33%;" />

不在配置类写,就可以自己在创建注入时指定要扫描的包

ps.xml中也可以声明扫描,之后使用 `ClassPathXmlApplicationContext` 驱动，也是可以获取到 `Person` 的。

````java
<context:component-scan base-package="com.linkedbear.spring.annotation.c_scan.bean"/>
<!-- 注意标签是package，不是packages，代表一个标签只能声明一个根包 -->
````

##### 组件注册的其他注解

SpringFramework 为了迎合咱在进行 Web 开发时的三层架构，它额外提供了三个注解：`@Controller` 、`@Service` 、`@Repository` ，分别代表表现层、业务层、持久层。这三个注解的作用与 `@Component` 完全一致，其实它们的底层也就是 `@Component` 



````java
@Target({ElementType.TYPE})
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Component
public @interface Controller { ... }
````

想注册,就加@Component,大同小异

有了这几个注解，那么在进行符合三层架构的开发时，对于那些 ServiceImpl ，就可以直接标注 `@Service` 注解，而不用一个一个的写 `<bean>` 标签或者 `@Bean` 注解了。

> 多提一嘴，其实 `@Repository` 是 SpringFramework 2.0 就已经有了的，只是到了 SpringFramework 3.0 才开始全面支持注解驱动开发。

##### @Configuration也是@Component

如果

上面指定的扫描包中，去掉后面的 bean ，让它扫描整个根包，咱修改一下启动类：

![image-20230424145059069](http://39.99.49.158/images/20230424/deda38d57d86.png)

运行 `main` 方法，会发现配置类 `ComponentScanConfiguration` 也被注册到 IOC 容器了：

可能会有小伙伴疑惑了，配置类不应该像配置文件那样，它只是做一个配置而已吗？咱看一眼 `@Configuration` 注解：

````java
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Component
public @interface Configuration { ... }
````

好吧，它也标注了 `@Component` 注解，证明确实它也会被视为 bean ，注册到 IOC 容器。

##### 注解驱动与xml驱动互通【掌握】

如果一个应用中，既有注解配置，又有 xml 配置，这个时候就需要由一方引入另一方了。两种方式咱都介绍一下。

######  xml引入注解

在 xml 中要引入注解配置，需要开启注解配置，同时注册对应的配置类：

````java
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd 
        http://www.springframework.org/schema/context 
        https://www.springframework.org/schema/context/spring-context.xsd">

    <!-- 开启注解配置 -->
    <context:annotation-config />
    <bean class="com.linkedbear.spring.annotation.d_importxml.config.AnnotationConfigConfiguration"/>
</beans>
````

###### 注解引入xml

在注解配置中引入 xml ，需要在配置类上标注 `@ImportResource` 注解，并声明配置文件的路径：

````java
@Configuration
@ImportResource("classpath:annotation/beans.xml")
public class ImportXmlAnnotationConfiguration {
    
}
````

#### 