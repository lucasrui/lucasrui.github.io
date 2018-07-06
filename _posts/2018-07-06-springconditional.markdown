---
layout: post
title:  "Spring注解@Conditional"
date:   2018-07-06 11:00:00 +0800
categories: SpringBoot 框架
---
@Conditional根据满足某个特定的条件创建一个特定的Bean，使用方法如下：
### 通过实现Condition接口，并重写其matches方法来构造判断条件
* 判断条件定义    
```java
public class LinuxCondition implements Condition {

	@Override
	public boolean matches(ConditionContext context, AnnotatedTypeMetadata metadata) {
		return context.getEnvironment().getProperty("os.name").contains("Linux");
	}
```
* 注解使用，在配置类中声明Bean
```java
@Bean
@Conditional(LinuxCondition.class)
public Object linuxService() {
	return new Object();
}
```

### Spring提供的其他Condition    
1. @ConditionalOnBean   
仅仅在当前上下文中存在某个对象时，才会实例化一个Bean。
2. @ConditionalOnClass    
某个class位于类路径上，才会实例化一个Bean
3. @ConditionalOnExpression   
当表达式为true的时候，才会实例化一个Bean。
```java
@ConditionalOnExpression("true")
@ConditionalOnExpression("${my.controller.enabled:false}")
```
4. @ConditionalOnMissingBean      
仅仅在当前上下文中不存在某个对象时，才会实例化一个Bean
5. @ConditionalOnMissingClass   
某个class类路径上不存在的时候，才会实例化一个Bean
6. @ConditionalOnNotWebApplication    
不是web应用
