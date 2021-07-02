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
    public void run() {
        System.out.println("Object type is  A");
    }
}
public class B extends A {
    char x = 'B';
    public void run() {
        System.out.println("Object type is B");
    }
}
```

### (1)  What would be result of

```java
A a = new A ();
B b = new B ();
A trick = new B();

System.out.println(a.x);
System.out.println(b.x);
System.out.println(trick.x);

a.run();
b.run();
trick.run();
```
```
A

B

A

Object type is A

Object type is B

Object type is B
```
`conclusion` late binding does not apply to instance variable but apply to instance methods 

You can extend (only one class) and then implement (any number of interfaces). Respectively. *Java doesn't have multiple inheritance*

### (2) For the following code :

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
        System.out.println ("can have 2 or 4 legs")
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

## Multiple Inheritance
You can extend (only one class) and then implement (any number of interfaces). Respectively. *Java doesn't have multiple inheritance*

## Final modifier

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
