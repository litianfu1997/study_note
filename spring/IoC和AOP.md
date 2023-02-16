# IoC和AOP

## 手写IoC

### 反射机制的基础知识

**获取Class对象的三种方式**

1. 类名.class

2. 对象.getClass()

3. Class.forName("全路径")

### 实例化

调用Class.newInstance()



### 获取所有构造

Constructor[] constructors = clazz.getConstructors()



**getConstructors()获取所有public的构造方法**

Constructor[] constructors = clazz.getConstructors();




**getDeclaredConstructors()获取包括private的构造方法**

Constructorr] constructors = clazz.getDeclaredConstructors();



**注意**

有**getDeclared**这个的可以获取私有的属性、方法、构造方法

配合setAccessible(true)可以对属性、方法、构造方法进行写操作



### 获取属性

获取所有public属性

Field[] fields = clazz.getFields();

获取所有属性包含私有属性
Field[] fields1 = clazz.getDeclaredFields();



### 获取方法

Method[] methods = clazz.getMethods();

使用invoke()方法可以对方法进行调用


