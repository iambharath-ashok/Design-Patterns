## Flyweight Design Pattern

-	Flyweight is a Structural Design Pattern 
-	Flyweight deals with memory issues
-	Flyweight DP reduces creating large number of similar objects
-	Flyweight DP reuses the already existing object

##  Ex: Drawing Shape of circle and rectangle

## 	Problem with out Flyweight Pattern

## 	Flyweight Implementation Steps

-	Separate the Extrinsic State
-	Pass them as Parameters
-	Create a Factory class

## Flyweight Implementation

	Code snippet:
	
		package flyweight;

		public abstract class Shape {
			public void draw(int radius, String fillColor, String lineColor) {

			}

			public void draw(int lenght, int breadth, String fillStyle) {

			}
		}

		class Circle extends Shape {
			private String lable = "Circle";

			public void draw(int radius, String fillColor, String lineColor) {
				System.out.println(lable + " : " + fillColor + lineColor + radius);
			}
		}

		class Rectangle extends Shape {
			private String lable ="Rectangle";

			public void draw(int lenght, int breadth, String fillStyle) {
				System.out.println(lable + lenght + breadth + fillStyle);
			}
		}

		public class PaintApp {

			public void drawShapes(int number) {
				Shape shape = null;
				for (int i = 1; i <= number + 1; i++) {
					if(i % 2 == 0) {
						shape = ShapeFactory.getShape("circle");
						shape.draw(i, "yellow", "pink");
					} else {
						shape = ShapeFactory.getShape("rectangle");
						shape.draw(i, i, "bharath");
					}
					
				}

			}
		}
		
		public class ShapeFactory {

			private static Map<String, Shape> cache = new HashMap<>();

			public static Shape getShape(String type) {
				Shape shape = null;
				if (cache.containsKey(type)) {
					shape = cache.get(type);
				} else {
					if (type.equals("circle")) {
						shape = new Circle();
					} else if (type.equals("rectangle")) {
						shape = new Rectangle();
					}
					cache.put(type, shape);
				}
				return shape;
			}
		}
			
		public class TestFlyweight {
			public static void main(String[] args) {
				PaintApp app = new PaintApp();
				app.drawShapes(10);
			}
		}	


