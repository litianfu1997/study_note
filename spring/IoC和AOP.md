# IoC��AOP

## ��дIoC

### ������ƵĻ���֪ʶ

**��ȡClass��������ַ�ʽ**

1. ����.class

2. ����.getClass()

3. Class.forName("ȫ·��")

### ʵ����

����Class.newInstance()



### ��ȡ���й���

Constructor[] constructors = clazz.getConstructors()



**getConstructors()��ȡ����public�Ĺ��췽��**

Constructor[] constructors = clazz.getConstructors();




**getDeclaredConstructors()��ȡ����private�Ĺ��췽��**

Constructorr] constructors = clazz.getDeclaredConstructors();



**ע��**

��**getDeclared**����Ŀ��Ի�ȡ˽�е����ԡ����������췽��

���setAccessible(true)���Զ����ԡ����������췽������д����



### ��ȡ����

��ȡ����public����

Field[] fields = clazz.getFields();

��ȡ�������԰���˽������
Field[] fields1 = clazz.getDeclaredFields();



### ��ȡ����

Method[] methods = clazz.getMethods();

ʹ��invoke()�������ԶԷ������е���


