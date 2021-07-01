# CS4-notes
notes for cs4 game course 

## final modifier

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
public class B extends A {
    char c = 'B'
    public void run {
        System.out.println("Object type is B");
    }
}
```

what would be result of 

```java
A a = new A ();
B b = new B ();
A trick = new B();

System.out.println(a.x);
System.out.println(b.x);
System.out.println(trick.x);

a.run;
b.run;
trick.run
```
results are 
A

B

A



Object type is A\

Object type is B\

Object type is B\

`conclusion` late binding does not apply to instance variable but apply to instance methods 


