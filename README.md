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


example - 

class TestClient3{

  static void info(Greeting impl){

    TestClient2.info(new RatanImpl());

    TestClient2.info(new RatanImpl());
    
  }
  
}

- The method "info" will handle all the implemintation classes. "Greeting" is the parent class.
