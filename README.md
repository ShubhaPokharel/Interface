# Interface

- Interfaces are by default abstract, so you cant create the object. They also contain the declaration part.

- The methods are by default public in interfaces, so when overriding, we must set the methods as public methods.


1. Interfaces are by default abstract.

2. Interface methods are by default public and abstract.

3. Interface variables re by default public, static and final.


##### Quick remainder:

###### class extends class

###### class implements interface

###### interface extends interface

Example -

interface Greeting{

  void greet();

  String name = "Pittsburgh";
  
}

class RatanImpl implements Greeting {

  public void greet(){

    System.out.println("Good morning - " + Greeting.name);
    
  }
  
}

class ShubhaImpl implements Greeting{

   public void greet(){

    System.out.println("Very Good morning - " + Greeting.name);
    
  }
}

class TestClient{

  public static void main(String[] args){

    RatanImpl ratan = new RatanImpl();

    ratan.greet();

    ShubhaImpl shubha = new ShubhaImpl();

    shubha.greet();
    
  }
  
}


Example -

interface Greeting{

  void greet();

  String name = "Shubha";
  
}

class RatanImpl implements Greeting {

  public void greet(){

    System.out.println("Good morning - " + Greeting.name);
    
  }
  
}

class ShubhaImpl implements Greeting{

   public void greet(){

    System.out.println("Very Good morning - " + Greeting.name);
    
  }
}

class Test{

  public static void main(String[] args){

    RatanImpl ratan = new RatanImpl();

    ratan.greet();

    ShubhaImpl shubha = new ShubhaImpl();

    shubha.greet();
    
  }
}

class TestClient2{

  static void info1(RatanImpl impl){

    impl.greet();
    
  }
    
  static void info2(ShubhaImpl impl){

    impl.greet();
    
  }

  public static void main(String[] args){

    TestClient2.info(new RatanImpl());

    TestClient2.info(new ShubhaImpl());
    
  }
  
}


We have 2 implemintation classes, so we took 2 methods. If we have 5 implemintation classes, we use 5 methods. If we want one method to handle all the implemintation classes, we can use "Greeting". "Greeting" is like the parent type for all the implemintation classes.


Note:

If you take the argument as the child classes, while calling the method we can only pass that child type. If you take the argument as the parent classes, while calling the methods we can pass all child types.


example - 

class TestClient3{

  static void info(Greeting impl){

    TestClient2.info(new RatanImpl());

    TestClient2.info(new RatanImpl());
    
  }
  
}

- The method "info" will handle all the implemintation classes. "Greeting" is the parent class.


##### Quick remainder:

###### class extends class

###### class implements interface

###### interface implements interface

_______________________

Case 1 - one interface can extend another interface

ex:

interface It1{

  void m1();

}

interface It2 extends It1{

  void m2();
  
}

interface It3 extends It2{

  void m3();
  
}

class Test implements It3{

  // override 3 methods
  
}


Case 2- One interface can extend multiply interface. But one class cannot extend multiple classes.

interface It1{

  void m1();

}

interface It2 extends It1{

  void m2();
  
}

interface It3 extends It1, It2{

  void m3();
  
}

class Test implements It3{

  // override 3 methods
  
}

Case 3- If multiple interfaces are having the common method, we can override that method once in the implemintation class.

ex:

interface It1{

  void m1();

  void m2();
  
}

interface It2{

  void m2();

  void m3();
  
}

interface It3{

  void m4();
  
}

class Test implements It3{

  // override 4 methods
  
}

Case 4- one class can implements multiple interfaces

interface It1{

  void m1();
  
}

interface It2{

  void m2();
  
}

interface It3{

  void m3();
  
}

class Test implements It1, It2, It3{

  // override 3 methods
  
}

case 5- If one class implements multiple interfaces, if the multiple interfaces are having the common method then override that method once in the implemintation class.

interface It1{

  void m1();

  void m2();
  
}

interface It2{

  void m2();

  void m3();
  
}

class Test implements It1, It2{

  //override 3 methods
  
}


1. One interface can extend another interface.

2. One interface can extend multiple interfaces.

3. One class can implement one interface.

4. One class can implement multiple interfaces.



example :

interface Operations{

  void add(int num1, int num2, int num3);

  void mul(int num1, int num2);
   
}

abstract class Dev1 implements Operations{

  public void add(int num1, int num2, int num3){

    System.out.println(num1 + num2 + num3);
    
  }

}

class Dev2 extends Dev1{

  void mul(int num1, int num2){

    System.out.println(num1 * num2);
    
  }
  
}

class Test{

  public static void main(String[] args){

    // Operations op = new Operations();  error: Operations is abstract; cannot be instaniated

    // Dev1 d1 = new Dev1(); error: Dev1 is abstract; cannot be instaniated

    Dev d2 = new Dev2();

    d2.add(10,20,30);

    d2.mul(30,60);
    

  }
  
}

- Operations has 2 methods. "Dev1" is supposed to handle those 2 methods but it is only handling one method. Because it isnt handling those 2 methods, it is an incomplete class. So, we need to turn it into an abstract class. "Dev2" handles the other method.

________________________

1. We use abstraction in interfaces if the class. So, there is no diffrence between interfaces and abtstraction because we use abstraction in interfaes.

Case 1-

interfae Servlet{

  //has 5 methods

  init() service() destroy() gsi() gsc()
  
}

- In case 1 we can override 5 methods. We will PROVIDE the implementations for the 5 methods.


Case 2-

interface Servlet{

    init() service() destroy() gsi() gsc()
    
}

abstract class GenericServlet implements Servlet{

    init(){} service(); destroy(){} gsi(){} gsc(){}
    
}

- In case 2, we have 5 methods in the interface. But, in the "GenericServlet" class it is only overriding 4 methods only. So, we make it an abstract class.

  ##### Security Logics

  Task - Lets say you want other classes to access your methods but only the classes that are extending your class.

Ex:

abstract class Ratan{

  void secure(){

    System.out.println("security code 7576");
    
  }

}

class Shubha extends Ratan{

  public static void main(String[] args){

    Shubha se = new Shubha();

    se.secure();
    
  }
  
}

This example is secure because the parent class is abstract. The only classes that can access the parent classes methods are the classes that are extending the parent class.

## Cloning Process

Cloning the object will take less time. Cloning is specific so we have to use a particular class name.

When we are cloning, we will exception. Even if we handled the exception, we still get the exception. To completly handle the class, we use "implements Cloneable".

The Cloneable interface is the Marker interface. The Marker interface contains no methods, but our class gets some capabilites from the class.


_________________

package com.pnc.bank;

interface Animal{

	void swim();
 
	void fly();
 
}

class Parrot implements Animal{

	public void swim() {
 
		System.out.println("parrot cant swim");
  
	}
 
	public void fly() {
 
		System.out.println("parrot can fly");
  
	}
 
}

class Penguin implements Animal{

	public void swim() {
 
		System.out.println("penguin can swim");
  
	}
	public void fly() {
 
		System.out.println("penguin cant fly");
  
	}
}
public class Practice {
	
	public static void animalInfo(Animal p) {
 
		p.fly();
  
		p.swim();
  
	}

	public static void main(String[] args) {
 

		Practice.animalInfo(new Parrot());
  
		Practice.animalInfo(new Penguin());
  

	}

}






