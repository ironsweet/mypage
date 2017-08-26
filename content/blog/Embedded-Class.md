---
title: Embedded Class
date: '2013-10-26'
description:
categories:
- 技术
tags:
- Java
- Go

---
Java里面的嵌套类，是指定义在某个类中，但却没有静态关键字的内部类。这种类的可读性很差，因为其方法可以访问到父类实例中的字段，而且申明的时候必须连带父类的名字一起才可以。除非是想逐步地拆分一个超级大类，否则实在很难想出为什么要使用内部类。在迁移一个内部类到Go语言的过程中，我使用了组合的方式，比如说

	type SubClass struct {
		*ParentClass
	}

这样，我就可以“肆无忌惮”的调用父类实例中的方法和字段。组合是在Go语言中被大量使用的，并且可以替代对象继承的方法。一个在Java语言中奇怪的用法，对应到了Go语言中则变得如此的自然。那如果反过去看呢？Java的内部类实际上是组合了父类对象的一种用法，可惜这种关系只是一对一的。