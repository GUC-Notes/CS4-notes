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
    char c = 'B'
    public void run {
        System.out.println("Object type is B");
    }
}
```

what would be result of?

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
