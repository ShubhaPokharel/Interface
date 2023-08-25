# Interface

- Interfaces are by default abstract, so you cant create the object. They also contain the declaration part.

- The methods are by default public in interfaces, so when overriding, we must set the methods as public methods.


1. Interfaces are by default abstract.

2. Interface methods are by default public and abstract.

3. Interface variables re by default public, static and final.


##### Quick remainder:

###### class extends class

###### class implements interface

###### interface implements interface

Example 1:

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


Example 2:

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


example 3- 

class TestClient3{

  static void info(Greeting impl){

    TestClient2.info(new RatanImpl());

    TestClient2.info(new RatanImpl());
    
  }
  
}

- The method "info" will handle all the implemintation classes. "Greeting" is the parent class.

example 4:

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
