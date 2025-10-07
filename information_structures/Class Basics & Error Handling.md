# Inheritance 

**Parent and children classes**

- Classes
	- Children classes inherit properties from the parent/super class
	- Attribute / field refer to variables contained within classes
	- "getter" and "setter" functions directly interact with attributes


*Syntax:*

In Circle.java:

	public class Circle extends Shape {
			int radius;
			public Circle(int x, int y, int radius){
				super(x, y)
			} f
		};

In Shape.java:

	public class Shape{
		int height;
		int width;
		public Shape(x, y){
			height = y;
			width  = x;
		}
	}



In java, child classes are able to over-write the methods from parent classes

NOTE:
- *Abstract* classes are parent classes that you cannot directly substantiate (cannot directly make an object of this class) 

		public class abstract Shape(){
			//Same as before
		}

- *Interface* is like a template for classes

		public interface ShapeInterface {
			public int getX();
			public int getY();
			public double getArea();
		}
Implementing an interface

	public class NewCircle implements ShapeInterface{ }

# Try and Except

- We use "try"  and "catch" block syntax

		try{
			int x = 1 / 0;
		}
		catch( Exception e ){
			System.out.println("You a failure")
		}
		finally{   // always runs -> even if catching the error did not work
			system.out.println("Finished program")
		}
**Exception Types**
- ArithmeticException e
- InputMismatchException e -> explicitly import java.util.Scanner

Add documentation using *JavaDoc format*  

 