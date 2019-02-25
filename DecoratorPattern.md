# Decorator Pattern

-	Decorator is a Behavioral Pattern that adds additional functionalities at runtime
-	Java IO packages uses Decorator Pattern 
-	Using Buffered Reader we can read more than one line at a time
-	All the classes in Java IO package implements Decorator Pattern
	
	EX:
		
		new BufferedReader(new FileReader());

## 	UML Diagram of Decorator Pattern

##	Decorator Pattern Implementation

	Code Snippet:
	
		package decorator;
		
		
		public interface Pizza {
	
			void bake();
		}

		class PlainPizza implements Pizza {
			
			public void bake() {
				System.out.println("Baking Plain Pizza");
			}
		}

		public class PizzaDecorator implements Pizza {
			private Pizza pizza;

			public PizzaDecorator(Pizza pizza) {
				this.pizza = pizza;
			}

			public void bake() {
				this.pizza.bake();
			}
		}

		class VegPizzaDecorator extends PizzaDecorator {

			public VegPizzaDecorator(Pizza pizza) {
				super(pizza);
			}

			public void bake() {
				super.bake();
				System.out.println("Adding Veggi Topings");
			}
		}

		class CheesePizzaDecorator extends PizzaDecorator {

			public CheesePizzaDecorator(Pizza pizza) {
				super(pizza);
			}

			public void bake() {
				super.bake();
				System.out.println("Adding Cheese Topings");
			}
		}

			
		
		public class PizzaDecoratorApp {

			public static void main(String[] args) {
				Pizza pizza =  new CheesePizzaDecorator(new VegPizzaDecorator(new PlainPizza()));
				pizza.bake();
			}
		}