# Composite Pattern

-	Composite Pattern is used where when we needs create a Object in Tree Structure
	-	When we want to build s/w in Tree Structure
	
-	Where one Object can have multiple objects and in turn objects with in  can have multiple objects
-	Whatever operation performed on leaf node should be able to perform on the composite node


## Implementation of Composite Pattern

	
	Code Snippet:
	
		public interface Component {

			void showPrice();
		}

		class Leaf implements Component {

			private final String name;
			private final double price;

			public Leaf(String name, double price) {
				this.name = name;
				this.price = price;
			}

			public void showPrice() {
				System.out.println(name + " : " + price);
			}
		}

		class Composite implements Component {

			private final String name;
			private List<Component> components = new ArrayList<Component>();
			
			
			public void addComponents(Component component) {
				this.components.add(component);
			}
			
			public Composite(String name) {
				this.name = name;
			}

			public void showPrice() {
				System.out.println(this.name);
				for(Component component : this.components) {
					component.showPrice();
				}
			}
		}
		
		public class TestComposite {
	
			public static void main(String[] args) {
				
				Component mouse = new Leaf("mouse",50);
				Component hdd = new Leaf("hdd",150);
				Component keyboard = new Leaf("keyboad",90);
				Component graphics = new Leaf("graphics",300);
				Component monitor = new Leaf("monitor",850);
				Component mb = new Leaf("mb",1850);
				
				//monitor.showPrice();
				
				Composite cabinet = new Composite("cabinet");
				cabinet.addComponents(hdd);
				cabinet.addComponents(graphics);
				cabinet.addComponents(mb);
				cabinet.showPrice();
				
				Composite prr = new Composite("prr");
				prr.addComponents(mouse);
				prr.addComponents(keyboard);
				prr.addComponents(monitor);
				prr.showPrice();
				
				Composite computer = new Composite("computer");
				computer.addComponents(prr);
				computer.addComponents(cabinet);
				computer.showPrice();
			}
		}
