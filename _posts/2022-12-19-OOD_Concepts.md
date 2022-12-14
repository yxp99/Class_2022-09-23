---
layout: post
title: OOD Concepts
date: 2022-12-19
author: Shadow Walker
tags: [OOD, OPLC]
toc: true
comments: true
---

## 要点

- 先确认需求, function 会写不会写先 放一边, OOP一定要考虑全. 每一个都问一下需不需要支持.
- 然后确认所有case, 一定要跟面试官确认所有的可能需求, 然后确认edge case.
- 最后再开始写代码. 千万不要着急写代码.
	- 先不要写function里面的东西, 把function**根据上面的需求一个一个都列出来**, retrun 和 parameter写出来. 
	- parameter 能用id用id, 用不了id, 再用string, int之类. 
	- 必须有**unique id**, 
	- 必须有增删改查. 
	- **Parameter**从用户角度出发
	- Service class应该是给所有用户共同调用, 而不是给每个客户都单独创建一个service.  
	- 考虑Service 的时候, 注意Service 应该是一个Singleton 一直在run, 而不是在被call的时候才突然启用. 
	- 注意var **命名规范, 多写注释.** OOD必须多解释, 不然面试官不懂在干什么. 
	- 注意区分var 类型, ENUM 还是 instant 还是 class var. 
	- Service 方法一定要写**public**. 
	
## SOLID Principles

- freeCodeCamp [guide](https://www.freecodecamp.org/news/solid-principles-single-responsibility-principle-explained/), Evernote [link](https://www.evernote.com/shard/s573/u/0/sh/d93688a9-fc91-4916-8e88-35612eca565a/6e503184122a3d0138dad22a6b5159ba)

## OOD related concepts

### Encapsulation

> Encapsulation in Java is a mechanism of wrapping the data (variables) and code acting on the data (methods) together as a single unit. In encapsulation, the variables of a class will be hidden from other classes, and can be accessed only through the methods of their current class. Therefore, it is also known as data hiding.

```java
public class EncapTest {
   private String name;
   private String idNum;
   private int age;

   public int getAge() {
      return age;
   }

   public String getName() {
      return name;
   }

   public String getIdNum() {
      return idNum;
   }

   public void setAge( int newAge) {
      age = newAge;
   }

   public void setName(String newName) {
      name = newName;
   }

   public void setIdNum( String newId) {
      idNum = newId;
   }
}
```

### Inheritance

> Inheritance can be defined as the process where one class acquires the properties (methods and fields) of another. With the use of inheritance the information is made manageable in a hierarchical order.

```java
class Calculation {
   int z;
	
   public void addition(int x, int y) {
      z = x + y;
      System.out.println("The sum of the given numbers:"+z);
   }
	
   public void Subtraction(int x, int y) {
      z = x - y;
      System.out.println("The difference between the given numbers:"+z);
   }
}

public class My_Calculation extends Calculation {
   public void multiplication(int x, int y) {
      z = x * y;
      System.out.println("The product of the given numbers:"+z);
   }
	
   public static void main(String args[]) {
      int a = 20, b = 10;
      My_Calculation demo = new My_Calculation();
      demo.addition(a, b);
      demo.Subtraction(a, b);
      demo.multiplication(a, b);
   }
}
```
### Polymorphism


Polymorphism is the ability of an object to take on many forms. The most common use of polymorphism in OOP occurs when a parent class reference is used to refer to a child class object.

```java
public interface Vegetarian{}
public class Animal{}
public class Deer extends Animal implements Vegetarian{}
```

### Abstraction

A class which contains the abstract keyword in its declaration is known as abstract class.

Abstraction is a process of hiding the implementation details from the user, only the functionality will be provided to the user. In other words, the user will have the information on what the object does instead of how it does it.

- Abstract classes may or may not contain abstract methods, i.e., methods without body ( public void get(); )

- But, if a class has at least one abstract method, then the class must be declared abstract.

- If a class is declared abstract, it cannot be instantiated.

- To use an abstract class, you have to inherit it from another class, provide implementations to the abstract methods in it.

- If you inherit an abstract class, you have to provide implementations to all the abstract methods in it.

```java
public abstract class Employee {
   private String name;
   private String address;
   private int number;

   public Employee(String name, String address, int number) {
      System.out.println("Constructing an Employee");
      this.name = name;
      this.address = address;
      this.number = number;
   }
   
   public double computePay() {
     System.out.println("Inside Employee computePay");
     return 0.0;
   }
   
   public void mailCheck() {
      System.out.println("Mailing a check to " + this.name + " " + this.address);
   }

   public String toString() {
      return name + " " + address + " " + number;
   }

   public String getName() {
      return name;
   }
 
   public String getAddress() {
      return address;
   }
   
   public void setAddress(String newAddress) {
      address = newAddress;
   }
 
   public int getNumber() {
      return number;
   }
}
```

```java
public class Salary extends Employee {
   private double salary;   // Annual salary
   
   public Salary(String name, String address, int number, double salary) {
      super(name, address, number);
      setSalary(salary);
   }
   
   public void mailCheck() {
      System.out.println("Within mailCheck of Salary class ");
      System.out.println("Mailing check to " + getName() + " with salary " + salary);
   }
 
   public double getSalary() {
      return salary;
   }
   
   public void setSalary(double newSalary) {
      if(newSalary >= 0.0) {
         salary = newSalary;
      }
   }
   
   public double computePay() {
      System.out.println("Computing salary pay for " + getName());
      return salary/52;
   }
}
```

```java
public class AbstractDemo {

   public static void main(String [] args) {
      Salary s = new Salary("Mohd Mohtashim", "Ambehta, UP", 3, 3600.00);
      Employee e = new Salary("John Adams", "Boston, MA", 2, 2400.00);
      System.out.println("Call mailCheck using Salary reference --");
      s.mailCheck();
      System.out.println("\n Call mailCheck using Employee reference--");
      e.mailCheck();
   }
}
```

