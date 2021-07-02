# CS4-notes
Notes for CS4 game course 

> Please consider contributing

## Final modifier

If you won't a method to be overridden.
``` java
public final void doSomething(){

}
```

If you don't want a class to be inherited, you can use the final
modifier too.

```java
public final class Hello{
    ...
}
```

## Refrence type vs Object type
   refrence type is the type written before equal and object type is the type we call constructor from it
```java 
public class A {
    char x = 'A';
    public void run {
        System.out.println("Object type is  A");
    }
}
```
```java
public class B extends A {
    char x = 'B'
    public void run {
        System.out.println("Object type is B");
    }
}
```

##### what would be result of?

```java
A a = new A ();
B b = new B ();
A trick = new B();
```

```java
System.out.println(a.x);
System.out.println(b.x);
System.out.println(trick.x);

System.out.println("------");

a.run();
b.run();
trick.run();
```
Results are 
```
A
B
A
------
Object type is A
Object type is B
Object type is B
```
`conclusion` late binding does not apply to instance variable but apply to instance methods 

`Please Note:` late binding can be applied to static variables.

You can extend (only one class) and then implement (any number of interfaces). Respectively. *Java doesn't have multiple inheritance*


#### For the following code :

```java

public class A {  
    char x = 'A';  
    public void run() {  
        System.out.println("runA");  
    }  
    public void run2() {  
        System.out.println("run2A");  
    }  
} 

public class B extends A {  
    char x = 'B';  
  
    public void run() {  
        System.out.println("runB");  
    }  
  
    public void run3() {  
        System.out.println("run3B");  
    }  
}

public static void main(String[] args) {  
    A trick = new B();
	
	// Code block inserted here 
}
```
#### What would be the result of :
```
trick.run();
```
```
trick.run2();
```
```
trick.run3();
```
#### Results are :
```
runA
```
```
runB
```
```
// compile error
cannot find symbol
	symbol:   method run3()
	location: variable trick of type Main.A
```

## Type Casting 
```java 
public class Animal {
    public void run (){
        System.out.println ("can have 2 or 4 legs");
    }
}
```
```java
public class FourLegsAnimal extends Animal {
    public void run (){
        System.out.println("actually has 4 legs");
    }
}
```
```java 
public class Dog extends FourLegsAnimal{
    public void run (){
        System.out.println("It's a dog");
    }
}
```
what would be the output of 
```java
Animal d = new Dog ();
d.run();
((Animal) d).run();
((FourLegsAnimal) d).run();
```
Output is 
It's a dog

It's a dog 

It's a dog 

`conclusion` type cast does not affect method calls (it will be called from object type class) 

What about 
```java
Animal a = new FourLegsAnimal();
((Dog) a).run();
```
it will give a run time error cannot cast from FourLegsAnimal to Dog 
`Note` you can not type cast to lower class (sub class) (`important` lower Class means lower class of object type). 
let's Add 
```java 
public class TwoLegsAnimal extends Animal {
    public void run (){
        System.out.println("actually has 2 legs");
    }
}
```
The OutputOf 
```java
FourLegsAnimal a1 = new FourLegsAnimal();
Animal a2 = new FourLegsAnimal();
((TowLegsAnimal) a1).run();
((TowLegsAnimal) a2).run();
```
```
Compile error 
RunTime Error
```
`impportant` you cannot type cast 2 classes in different branches , compile error depend on referenceType but runTimeErroe depends on ObjectType

## Multiple Inheritance
You can extend (only one class) and then implement (any number of interfaces). Respectively. *Java doesn't have multiple inheritance*

## Cases of Type Casting

```java
		Person p = new Person();
		Student s = new Student(); // Student extends Person
		Teacher t = new Teacher(); // Teacher extends Person
		
		Person ps = new Student();
		Person pt = new Teacher();
		
		Student sp = new Person(); // compilation error
		Student st = new Teacher(); // compilation error
	
		Teacher tp = new Person(); // compilation error
		Teacher ts = new Student(); // compilation error

		System.out.println((Student) p); // run time error
		System.out.println((Teacher) p); // run time error
		
		System.out.println((Person) s);
		System.out.println((Teacher) s); // compilation error
		
		System.out.println((Person) t);
		System.out.println((Student) t); // compilation error
		
		
		System.out.println((Person) ps);
		System.out.println((Student) ps);
		System.out.println((Teacher) ps); // run time error
		System.out.println((Person) pt);
		System.out.println((Student) pt); // run time error
		System.out.println((Teacher) pt);
```



## Inheritance 

What is the **OUTPUT** of the following **CODE**

```java
public class Parent{
    public void c1(){
	    System.out.print("1");
    	c2();
    }
    public void c2(){
    	System.out.print("2");
    }
}
public class Child extends Parent{
    public void c1(){
	    super.c1();
    	System.out.print("3");
    }
    public void c2(){
    	super.c2();
    	System.out.print("4");
	}
    public static void main(String [] args){
		Parent p = new Child();
        p.c1();
    }
}
```
**OUTPUT:** 1243

In inheritance, you inherit all the public and private instance variables, but you can only access the public ones. 

## Exceptions

The following code will not compile the NullPointerException catch block is unreachable because NullPointerException is a subClass of Exception

```java
public void method(){
    try{
        //Something
    } catch (Exception e){
        //Something
    } catch (NullPointerException e) {
        //Something
    }
}
```
While the following code will compile and run since because the compiler can't see that the second catch block is unreachable

```java
public void method(){
    try{
        //Something
    } catch (Exception e){
        //Something
    }
}
public void methodCaller(){
    try{
        method()
    } catch (NullPointerException e){
        //Something
    }
}

```

## Abstraction 

The abstract methods in any abstract class must be defined once the subclass is not Abstract. Meaning that if an abstract class extends another abstract one you cannot have a body for the method in either class :) 

## Interfaces 

1. Any method written in an interface is set to be (public) by default.
2. You can never use the word **new** before an interface or an abstract class name, but you can the name of the interface itself to have objects of that type. See below
```java

// Assume we have an interface/abstract class called Person, 
and a class Student that extends person.

Person myPerson = new Person(); // This is wrong XXX.
Person myPerson = new Student(); // This is okay.


```

3. An interface can't have instance variables (by logic because we can't make instances of it) but it may have static variables.  

## Encapsulation :

1. A private constructor = you cannot instantiate an object from that class. 
2. You can't override public methods in the parent class with a private ones in the child class.
Overriding (children) has to be less restrictive ! 
OR the parent has to be more strict ;) 
private -> default -> protected -> public.
from high to low restriction. 

### Access Modifiers Summary: 
1. public: Members available everywhere
2. private: Members available only in the class
3. default: Members available in the same class,package only.
4. protected: Members available in the same class,package and another package but a subclass of this class. 
**Note**: default is more protected than the protected access modifier :O 


