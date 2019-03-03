# Bridge Design Pattern

-	Bridge design pattern is one of the Structural design pattern
-	When we have interface hierarchies in both interfaces as well as implementations
-	Then bridge design pattern is used to decouple the interfaces from implementation 
-	By hiding the implementation details from the client programs
-	According to GoF bridge design pattern is:

	-	Decouple an abstraction from its implementation so that the two can vary independently
	

	
## Bridge Pattern Definition


-	In the bridge pattern, there are 2 parts the first part is Abstraction and second part is implementation
-	Bridge pattern Abstraction and implementation part to be developed independently
-	Client code can access only the Abstraction part without being concerned about the implementation part


-	Bridge Pattern separates the abstraction heirarchy and the implementation heirarchy in two different layers 
-	So that change in one heirarchy will not affect the development or functionality of other heirarchy



## Use cases of Bridge Pattern

-	Persistance with two different Implementations like DB, File, XML etc...
-	Shape and filling the color


## Bridge Pattern Implementations with Shape Usecase


-	The bridge between Shape and Color interfaces and use of composition in implementing the bridge pattern



	Code Snippet:
	
		package bridge;

		public abstract class Shape {
			protected Color c;

			public abstract void applyColor();

			protected Shape(Color c) {
				this.c = c;
			}
		}

		class Triangle extends Shape {

			public Triangle(Color c) {
				super(c);
				this.c = c;
			}

			public void applyColor() {
				c.fillColor();
			}
		}

		class Circle extends Shape {

			public Circle(Color c) {
				super(c);
				this.c = c;
			}

			public void applyColor() {
				c.fillColor();
			}
		}



		package bridge;

		public interface Color {
			void fillColor();
		}

		class RedColor implements Color {

			public void fillColor() {
				System.out.println("Filling Red Color");
			}
		}

		class BlueColor implements Color {

			public void fillColor() {
				System.out.println("Filling Blue Color");
			}
		}

		class GreenColor implements Color {

			public void fillColor() {
				System.out.println("Filling Green Color");
			}
		}



		public class BridgeTest {

	
			public static void main(String[] args) {
				
				Shape triangle = new Triangle(new RedColor());
				triangle.applyColor();
			}
		}






















