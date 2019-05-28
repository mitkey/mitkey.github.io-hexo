---
title: Object的clone方法
tags:
  - Dev
  - Clone
categories:
  - Java
  - Object
comments: false
date: 2019-04-29 11:15:11
updated: 2019-04-29 11:15:11
password:
---

如何复制对象？使用 Object 的 clone 方法复制对象，需要注意哪些地方？

<!-- more -->

## QAQ

- 为什么对象的 clone 方法不能访问的？因为在 Object 中默认是 protected 权限的

- 如何覆写 clone 方法？调用 super.clone() 即可（Object 内部实现的 native）

- 为什么覆写了 clone 方法，还是不能访问并且抛出异常 java.lang.CloneNotSupportedException？未实现 Cloneable 接口

- 克隆的对象是同一个内存地址吗？不是，可以使用 Object.toString 方法打印内存地址

## 解析
该 clone 方法（Object.clone）效果等价于，对每个字段进行 getting setting 而已。
引用类型字段值在克隆后新对象中的对应字段是同一个引用。

	
	public class TestA implements Cloneable {
		private int age;
		private TestB testB;

		public TestA(int age, TestB testB) {
			this.age = age;
			this.testB = testB;
		}

		@Override
		public Object clone() throws CloneNotSupportedException {
			return super.clone();
		}

		public int getAge() {
			return age;
		}

		public void setAge(int age) {
			this.age = age;
		}

		public TestB getTestB() {
			return testB;
		}

		public void setTestB(TestB testB) {
			this.testB = testB;
		}

		@Override
		public String toString() {
			return "TestA [age=" + age + ", testB=" + testB + ", toString()=" + super.toString() + "]";
		}
	}

	public class TestB implements Cloneable {
		private int no;
		private String className;

		public TestB(int no, String className) {
			this.no = no;
			this.className = className;
		}

		public int getNo() {
			return no;
		}

		public void setNo(int no) {
			this.no = no;
		}

		public String getClassName() {
			return className;
		}

		public void setClassName(String className) {
			this.className = className;
		}

		@Override
		public String toString() {
			return "TestB [no=" + no + ", className=" + className + ", toString()=" + super.toString() + "]";
		}

	}

	public static void main(String[] args) throws Exception {
		TestA testA = new TestA(15, new TestB(1, "哈哈哈"));
		TestA clone = (TestA) testA.clone();

		// TestB 对象的内存地址一致
		System.err.println(testA.getTestB());
		System.err.println(clone.getTestB());

		// TestA 内存地址不一致
		System.err.println(testA);
		System.err.println(clone);

		testA.getTestB().setClassName("默默");
		// 都是 默默
		System.err.println(testA.getTestB().getClassName());
		System.err.println(clone.getTestB().getClassName());
	}

运行后发现，不会报错。说明 Object.clone 方法克隆时，对象不需要提供无参的构造方法

## 忽略点

内部字段若是引用类型的，复制的新对象与源对象共用的是同一个引用
	
 