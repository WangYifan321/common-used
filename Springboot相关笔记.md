# Springboot

## 文件的配置

如果某一个字段是字符串类型的不用带双引号，带上的话无所谓，里面有\n的话会换行，如果是单引号表示字符串杠n不会换行

### @value获取值和@ConfigurationProperties获取值的比较

|                         | @ConfigurationProperties        | @value           |
| ----------------------- | ------------------------------- | ---------------- |
| 功能                    | 支持批量注入配置文件的属性      | 必须一个一个注入 |
| 松散绑定（松散语法）    | 支持（lastName等价于last-name） | 不支持           |
| SpEL                    | 不支持                          | 支持             |
| jsr303数据校验          | 支持                            | 不支持           |
| 复杂类型的封装（map等） | 支持                            | 不支持           |

SpEL值得是嵌入在@value里的一些运算表达式

jsr303数据校验：例如把@email加在一个字段前面可以判定这个字段必须是Email格式的，否则将会报错

​      如果说，我们只是在某个业务逻辑中需要获取一下配置文件中的某一项的值用@value（"${字段名}"）加在变量的定义之前

​      如果说，我们专门编写了一个JavaBean来和配置文件进行映射，我们就直接用  @ConfigurationProperties

@propertySource(locations={"classpath:  "})   @importResource标在主配置类上psvm那个class中 @bean

### profiles

1. 可以在properties的文件中指定spring.profiles.active=dev     创建好了另一个测试的配置文件后命名为application-dev.properties   激活后则会用另一个的配置 文件

2.  在yml文件中   ---可以把文档分区,文档块模式，只有被激活配置文件才会生效

   ```yaml
   server: 
     port: 8087
   spring: 
     profiles: 
         active: dev
   ---
   server: 
     port: 8083
   spring: 
     profiles: dev
   ```

   3. 把spring boot打成jar包之后，可以在cmd窗口下，Java -jar  jar包名 --spring.profiles.active=dev

      

      

      

  ### 配置文件的优先级（配置加载)

-file:config   >     -file   >    classpath: /config  >  classpath

classpath即为idea默认下的resource文件夹下

**这些配置文件是互补配置，先优先加载高优先级的配置文件，如果高优先级的配置文件有些不全，可以加载低优先级的**

**浏览器的访问路径可以在配置文件中指定，server.context-path=/boot02  在浏览器的地址栏中必须输入/boot02/hello**

**达成jar包之后，可以在cmd窗口中指定配置文件的加载路径，常用于后期的测试和更改，原先的配置文件也会生效但这个的优先级更高------spring.config.location=路径**

可以直接在cmd窗口中输入参数，--server.port:   这个的优先级是最高的

jar外部带profile> jar内部带profile>jar外部不带profile> jar内部不带profile

达成jar包后在同一个文件下的带profile的文件是有优先级高的，不带的优先级相对低   ，，

profile其实就是application-dev。properties或者yaml文件中的spring：profile （active）的这种格式



### 查看自动配置

配置文件中加入

debug=true    默认下是false

## 日志

```java
Logger lo = LoggerFactory.getLogger(getClass());
    @Test
    public void contextLoads02(){
        lo.trace(()->{
            return "这是一个trace日志";
        });
        lo.debug(()->{
            return "这是一个debug日志";
        });
        //spring默认是info级别的
        lo.info(()->{
            return "这是一个info日志";
        });
        lo.warn(()->{
            return "这是一个warn日志";
        });
        lo.error(()->{
            return "这是一个error日志";
        });

    }
```

logging.level.com.包名=trace  这个可以指定日志的等级

### 指定日志的输出地

默认情况下日志只会在控制台输出，配置文件中logging.file=spring.log在当前目录下生成日志，可以写上具体路径，logging.path=/ spring  /log  可以指定路径，在磁盘的根目录下创建spring文件夹（新版已经不是这样的）

### 指定日志的输出格式

```java 
在配置文件中：
    logging.pattern.console=%d{yyyy-MM-dd HH:mm:ss.SS} [%thread] %-5level %logger{50} - %msg%n
    logging.pattern.file=        

2020-04-11 14:44:15.768 DEBUG 9628 --- [           main] com.example.demo.DemoApplicationTests    : 这是一个trace日志

%d{yyyy-MM-dd HH:mm:ss.SS} [%thread] %-5level %logger{50} - %msg%n
    
    %d表示日期时间
    %thread表示线程名
    %-5level级别从左显示5个字符宽度
    %logger{50}表示logger名字最长50个字符，否则按照句点分割
    %msg日志消息
    %n换行符    
```



## 类路径的根目录就是resource是文件



## Springboot与web开发

静态资源文件夹

​         class path：1. /META-INF/resources/

/resources在resources文件夹下

 /static/本来就存在，resources文件夹中

/public/在resources文件夹下

当前项目的根路径

若要导入外部的js，需要写入依赖

```java 
 <dependency>
            <groupId>org.webjars</groupId>
            <artifactId>jquery</artifactId>
            <version>3.3.1</version>
        </dependency>
```

导入后即可访问，注意默认的文件夹是resources，所以浏览器访问时不用加/resources

***默认的首页在静态资源文件夹中的index.html中***

  ## thymeleaf相关使用

```java
 <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-thymeleaf</artifactId>
        </dependency>
```

# Mybatis

mapper：相当于dao层，编写访问数据库的接口

pojo：存放实体类

resource-mybatis-mapper-***.xml：用于存放配置文件，编写sql语句

pom.xml：引入相关的依赖

properties：编写配置文件路径

```yaml
mybatis:
  type-aliases-package: com.example.demo.pojo
  mapper-locations: classpath:mybatis/mapper/*.xml
```

# swagger

相关的依赖

```
        <!-- https://mvnrepository.com/artifact/io.springfox/springfox-swagger-ui -->
        <dependency>
            <groupId>io.springfox</groupId>
            <artifactId>springfox-swagger-ui</artifactId>
            <version>2.9.2</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/io.springfox/springfox-swagger2 -->
        <dependency>
            <groupId>io.springfox</groupId>
            <artifactId>springfox-swagger2</artifactId>
            <version>2.9.2</version>
        </dependency>
```



编写配置类，配置swagger的页面信息

```java
@Configuration
@EnableSwagger2
public class SwaggerConfig {
    @Bean
    public Docket docket(){
        return new Docket(DocumentationType.SWAGGER_2)
                .select()
                .apis(RequestHandlerSelectors.basePackage("com.example.demo.controller")).
                build().apiInfo(apiInfo());
    }
    private ApiInfo apiInfo(){
        Contact contact = new Contact("王一凡","","877801903@qq.com");
        return new ApiInfo("创新实践HDU-ZHI API文档",
                "创新实践2作业，HDU-ZHI项目文档",
                "1.0",
                "urn:tos",
                contact,
                "Apache 2.0", "http://www.apache.org/licenses/LICENSE-2.0", new ArrayList());
    }

}
```



# 开启异步

spring boot主启动类上加上注解，@enableasync。在service层可以开启异步，@async。即可异步执行代码

# 邮件

引入mail的依赖

```
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-mail</artifactId>
        </dependency>
```

配置文件中

```java
spring.mail.username=877801903@qq.com
spring.mail.password=acjskcc
    #qq邮箱中可以获得
spring.mail.host=smtp.qq.com
spring.mail.properties.mail.smtl.ssl.enable=true
#开启加密认证
```

```java
//现在业务或者测试类中注入
@Autowired
JavaMailSenderImpl mailSender;
```



![QQ截图20210310221307](C:\Users\wkjiaju\Desktop\QQ截图20210310221307.png)

# 定时任务

```
@enablescheduling
主启动类上开启定时的注解
```

在业务层service中的类中的方法上加上注解@scheduled(cron = "表达式")

# jpa

```
<dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>

```



## 配置文件

```
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/mytest
    type: com.alibaba.druid.pool.DruidDataSource
    username: root
    password: root
    driver-class-name: com.mysql.jdbc.Driver //驱动
  jpa:
    hibernate:
      ddl-auto: update //自动更新
    show-sql: true  //日志中显示sql语句
```

```
jpa.hibernate.ddl-auto是hibernate的配置属性，其主要作用是：自动创建、更新、验证数据库表结构。该参数的几种配置如下：
    ·create：每次加载hibernate时都会删除上一次的生成的表，然后根据你的model类再重新来生成新表，哪怕两次没有任何改变也要这样执行，这就是导致数据库表数据丢失的一个重要原因。
    ·create-drop：每次加载hibernate时根据model类生成表，但是sessionFactory一关闭,表就自动删除。
    ·update：最常用的属性，第一次加载hibernate时根据model类会自动建立起表的结构（前提是先建立好数据库），以后加载hibernate时根据model类自动更新表结构，即使表结构改变了但表中的行仍然存在不会删除以前的行。要注意的是当部署到服务器后，表结构是不会被马上建立起来的，是要等应用第一次运行起来后才会。
    ·validate：每次加载hibernate时，验证创建数据库表结构，只会和数据库中的表进行比较，不会创建新表，但是会插入新值。
```

## 常用的注解

注解	解释
**@Entity**	声明类为实体或表。
**@Table**	声明表名。
@Basic	指定非约束明确的各个字段。
@Embedded	指定类或它的值是一个可嵌入的类的实例的实体的属性。
**@Id**	指定的类的属性，用于识别（一个表中的主键）。
**@GeneratedValue**	指定如何标识属性可以被初始化，例如自动、手动、或从序列表中获得的值。@GeneratedValue(strategy = GenerationType.IDENTITY)声明主键
@Transient	指定的属性，它是不持久的，即：该值永远不会存储在数据库中。
**@Column**	指定持久属性栏属性。
@SequenceGenerator	指定在@GeneratedValue注解中指定的属性的值。它创建了一个序列。
@TableGenerator	指定在@GeneratedValue批注指定属性的值发生器。它创造了的值生成的表。
@AccessType	这种类型的注释用于设置访问类型。如果设置@AccessType（FIELD），则可以直接访问变量并且不需要getter和setter，但必须为public。如果设置@AccessType（PROPERTY），通过getter和setter方法访问Entity的变量。
@JoinColumn	指定一个实体组织或实体的集合。这是用在多对一和一对多关联。
@UniqueConstraint	指定的字段和用于主要或辅助表的唯一约束。
@ColumnResult	参考使用select子句的SQL查询中的列名。
@ManyToMany	定义了连接表之间的多对多一对多的关系。
@ManyToOne	定义了连接表之间的多对一的关系。
@OneToMany	定义了连接表之间存在一个一对多的关系。
@OneToOne	定义了连接表之间有一个一对一的关系。
@NamedQueries	指定命名查询的列表。
@NamedQuery	指定使用静态名称的查询



# redis

引入依赖

```

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-redis</artifactId>
        </dependency>
        <!-- https://mvnrepository.com/artifact/redis.clients/jedis -->
        <dependency>
            <groupId>redis.clients</groupId>
            <artifactId>jedis</artifactId>
            <version>3.3.0</version>
        </dependency>

光引入启动类即可
```

```yaml
spring: 
 redis:
    host: 47.111.190.15
    port: 6379
```

# 前后端日期格式得问题

```
@JsonFormat(pattern="yyyy-MM-dd HH:mm:ss",timezone = "GMT+8")
```

java.util.Date类型的格式是 Mon Aug 03 20:26:56 CST 2020
SimpleDateFormat和DateFormat的format方法可以将Date类型转换成字符串，但是对生成的字符串调用parse方法生成的Date类型还是原来那种 Mon Aug 03 20:26:56 CST 2020格式
可能有点绕，简而言之就是Date型只有一种格式，可以有多种字符串表示。



## linux后台启动jar包

转载自https://juejin.im/post/5b47411ee51d45190570ce6d

最终的运行命令：

```
nohup java -jar xxx.jar >logs.txt &



复制代码
```

下面再做详细分解介绍。

1.首先最基本的运行jar包命令是:

```
java -jar xxx.jar



复制代码
```

这个命令会锁定命令窗口，只能看到当前运行的输出信息。而无法发送其他指令。

2.让jar包后台运行

用"&"符号结尾表示，让程序在后台运行。
这样的话，命令窗口就不会被锁定，而可以发送其他指令，但是当窗口关闭时，后台运行的程序依然会被停止。

nohup命令：nohup 命令运行由 Command参数和任何相关的 Arg参数指定的命令，忽略所有挂断信号。要运行后台中的 nohup 命令，添加 & （ 表示“and”的符号）到命令的尾部。

简单地说就是，nohup命令可以阻止窗口关闭是的挂断信号，使程序继续运行。这样，命令就修改为了

```
nohup java -jar xxx.jar &



复制代码
```

3.设置输出文件

在这个命令下已经可以实现需要的功能了。最后的 >logs.txt 表示输出文件。可以随意写随意指定路径。如果不写情况下（缺省），就回默认在jar包所在目录，创建nohup.out文件。

如果项目中已经指定了日志输出，就会重复输出，生成两个文件，把 >logs.txt 删了的话，当前的运行程序不会再生成新的文件。

```
nohup java -jar xxx.jar >logs.txt &



复制代码
```

命令运行成功后，会返回一个进程号，可以通过 kill -9 命令杀死这个进程来直接关闭。

> 如果忘了进程号，可以通过
>
> ```
> ps -ef|grep xxx.jar
> 
> 
> 
> 复制代码
> ```
>
> 来查看当前运行的jar包程序进程号。







