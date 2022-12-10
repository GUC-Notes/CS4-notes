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
runB
```
```
run2A
```
```
// compile error
cannot find symbol
	symbol:   method run3()
	location: variable trick of type Main.A
```


### (3) For the following code:

```java

public class A {
	public void priv() {
		System.out.println("A");
	}
	public void printPriv(A a) {
		a.priv();
	}
}

public class B extends A {
	public void priv() {
		System.out.println("B");
	}
	public void printPriv(B b) {
		b.priv();
	}

	public static void main(String args[]) {
		A a = new A();
		B b = new B();

		a.printPriv(b);
	}
}
```
	
#### The result is:
```
B
```
#### but if we declare A with the priv method private instead of public:

```java
public class A {
	private void priv() {
		System.out.println("A");
	}
	public void printPriv(A a) {
		a.priv();
	}
}
```

#### The result is now:
```
A
```
