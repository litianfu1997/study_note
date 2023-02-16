# spring

## IOC容器

loC是Inversion of Control 的简写，译为“控制反转”，它不是一门技术，而是一种设计思想，是一个重要的面向对象编程法则，能够指导我们如何设计出松耦合、更优良的程序。
**Spring 通过ioc容器来管理所有Java 对象的实例化和初始化，控制对象与对象之间的依赖关系**。我们将由ioc容器管理的Java 对象称为 Spring Bean，它与使用关键字 new 创建的Java 对象没有任何区别。
loC容器是 Spring 框架中最重要的核心组件之一，它贯穿了 Spring 从诞生到成长的整个过程.

## IOC控制反转

* 控制反转是一种思想

* 控制反转是为了降低程序耦合度，提高程序扩展力。

* 控制反转，反转的是什么?
  
  * 将对象的创建权利交出去，交给第三方容器负责将对象和对象之间关系的维护权交出去，交给第三方容器负责
  
  * 控制反转这种思想如何实现呢?
    
    * DI (Dependency njection) : 依赖注入

![](C:\Users\sugon\Desktop\study_note\images\2023-02-16-09-13-41-image.png)

## DI依赖注入

指Spring创建对象的过程中，将**对象依赖属性**通过配置进行注入

依赖注入常见的实现方式包括两种:
第一种: set注入
第二种:构造注入

所以结论是: IoC 就是一种控制反转的思想，而 DI 是对IoC的一种具体实现

Bean管理说的是: **Bean对象的创建，以及Bean对象中属性的赋值(或者叫做Bean对象之间关系的维护)**

## IoC容器在spring的实现

Spring 的 loC 容器就是 loC思想的一个落地的产品实现。loC容器中管理的组件也叫做 bean。在创建 bean 之前，首先需要创建loC 容器。Spring 提供了loC 容器的两种实现方式:

1. **BeanFactory**
   这是loC 容器的基本实现，是 Spring 内部使用的接口。面向 Spring 本身，不提供给开发人员使用.

2. **ApplicationContext**
   BeanFactory 的子接口，提供了更多高级特性。面向 Spring 的使用者，几乎所有场合都使用 ApplicationContext而不是底层的 BeanFactory。

3. **ApplicationContext主要实现类**

![](C:\Users\sugon\Desktop\study_note\images\2023-02-16-09-31-36-image.png)

![](C:\Users\sugon\Desktop\study_note\images\2023-02-16-09-30-32-image.png)

## 基于注解管理bean

从Java 5 开始，Java 增加了对注解(Annotation)的支持，它是代码中的**一种特殊标记**，可以**在编译、类加载和运行时被读取**，执行相应的处理。开发人员可以通过注解在不改变原有代码和逻辑的情况下，在源代码中嵌入补充信息。
Spring 从 2.5 版本开始提供了对注解技术的全面支持，我们可以使用注解来实现自动装配，简化 Spring 的XML配置。
Spring 通过注解实现自动装配的步骤如下：

1. 引入依赖

2. 开启组件扫描

3. 使用注解定义 Bean

4. 依赖注入



### 使用注解定义bean

![](C:\Users\sugon\Desktop\study_note\images\2023-02-16-09-43-40-image.png)

### 使用@Autowired注入

单独使用@Autowired注解，默认**根据类型装配**。【默认是byType】

源码：

![](C:\Users\sugon\Desktop\study_note\images\2023-02-16-09-56-46-image.png)

**源码中有两处需要注意:**
第一处: 该注解可以标注在哪里?

* 构造方法上

* 方法上

* 形参上

* 属性上

* 注解上
  
  

第二处: 该注解有一个required属性，默认值是true，表示在注入的时候要求被注入的Bean必须是存在的如果不存在则报错。如果required属性设置为false，表示注入的Bean存在或者不存在都没关系，存在的话就注入，不存在的话，也不报错.

注意：如果一个接口有多个实现类，使用@Autowired注解会报错，因为@Autowired是通过类型匹配的，此时应该配合@Qualifier注解指定实现类名称（首字母小写）



![](C:\Users\sugon\Desktop\study_note\images\2023-02-16-10-11-55-image.png)





### 使用@Resource注解注入

**@Resource注解也可以完成属性注入。那它和@Autowired注解有什么区别?**
@Resource注解是JDK扩展包中的，也就是说属于JDK的一部分。所以该注解是标准注解，更加具有通用性(JSR-250标准中制定的注解类型。JSR是Java规范提案。)
@Autowired注解是Spring框架自己的。
**@Resource注解默认根据名称装配byName，未指定name时，使用属性名作为name。通过name找不到的话会自动启动通过类型byType装配。**
@Autowired注解默认根据类型装配byType，如果想根据名称装配，需要配合@Qualifier注解一起用。
@Resource注解用在属性上、setter方法上
@Autowired注解用在属性上、setter方法上、构造方法上、构造方法参数上



注意:

@Resource注解属于JDK扩展包，所以不在]DK当中，需要额外引入以下依赖: [**如果是]DK8的话不需要额外引入依赖。高于JDK11或低于JDK8需要引入以下依赖。**]

![](C:\Users\sugon\Desktop\study_note\images\2023-02-16-10-40-56-image.png)
