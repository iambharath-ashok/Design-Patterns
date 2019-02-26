## Factory Design Pattern


-	Factory DP is creational pattern which the object creation process 
-	EX : Car Factory, Chocolate Factory, Toy Factory
-	Need not worry about how Car is manufactured, just we will ask car manufacture to deliver some cars 
-	JDBC DriverManager class is a Factory Design Pattern, Driver can connect multiple DB's like Oracle, MySql, Sql Server
-	DriverManger.getConnection(String connectionString);
	
	Connection connection = DriverManger.connection(String connection);

EX: Pizza Store

-	Pizza Store Offers different types of Pizza
-	Pizza Store will ask the PizzaFactory for the diff type of Pizza
-	Pizza Store will not worry about creation of Pizza 
-	Pizza factory will hides the implementation details of Pizza Creation

	
Code Snippet of Pizza Store Factory:
		
		
	Code Snippet of Pizza:
		
		package factory;

		public interface Pizza {
			
			void createPizza();
			void bakePizza();
			void cutPizza();

		}

		public class PizzaFactory {

			public static Pizza getPizza(PizzaType type) {
				Pizza p = null;

				switch (type) {
				case VEG:
					p = new VegPizza();
					break;
				case CHICKEN:
					p = new ChickenPizza();
					break;
				default:
					break;
				}
				return p;
			}
		}
		
		public class PizzaStore {
		
			public void orderPizza(PizzaType type) {
				Pizza p = PizzaFactory.getPizza(type);
				p.createPizza();
				p.bakePizza();
				p.cutPizza();
			}

		}
		
		public enum PizzaType {
			VEG, CHICKEN;
		}
		
		public class VegPizza implements Pizza {
			@Override
			public void createPizza() {
				System.out.println("Preparing Veg Pizza");
			}
			@Override
			public void bakePizza() {
				System.out.println("Baking Veg Pizza");
			}
			@Override
			public void cutPizza() {
				System.out.println("Cutting Veg Pizza");
			}
		}
		
		
		public class TestFactory {
	
			public static void main(String[] args) {
				
				PizzaStore ps = new PizzaStore();
				ps.orderPizza(PizzaType.VEG);
			}
		}
