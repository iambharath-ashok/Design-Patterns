# Template Pattern

- 	Template Pattern is behavioral Pattern in which a base template will used by Child classes
-	During inheritance, child classes can inherit and provide implementation to other methods
-	But should use base template method in the parent class
-	EX: Data Rendering
	-	No matter in which format data comes in XML or JSON CSV .... application should return the data in specific format
	-	All the child classes should use the base template method to render the data in same format
	

## Template DP UML Diagram

## Template Implementation with Data Renderer


	Code Snippet:
	
		package template;

		public abstract class DataRenderer<T> {

			protected void render() {
				T data = readData();
				data = this.processData(data);
				System.out.println(data);
			}

			protected abstract T readData();

			protected abstract T processData(T data);

		}
		
		
		public class XmlDataRenderer<T> extends DataRenderer<T> {

			@SuppressWarnings("unchecked")
			@Override
			protected T readData() {
				return (T) "XML Data";
			}

			@SuppressWarnings("unchecked")
			@Override
			protected T processData(T data) {
				return (T) ("Processed " + data);
			}

		}
		
		
		public class JSONDataRenderer<T> extends DataRenderer<T> {

			@SuppressWarnings("unchecked")
			@Override
			protected T readData() {
				return (T) "JSON Data";
			}

			@SuppressWarnings("unchecked")
			@Override
			protected T processData(T data) {
				return (T) ("Processed "+ data);
			}
		}
		
		
		public class TestTemplatePattern {
	
		public static void main(String[] args) {
				DataRenderer<Integer> dr = new XmlDataRenderer<>();
				dr.render();
			}
		}
		
		
## Asignment:

	Code Snippet:
	
		public abstract class ComputerManufacturer<T> {
	
			protected void buildComputer() {
				T computer = null;
				computer = addHardDisk(computer);
				computer = addMotherBoard(computer);
				computer = addKeyboard(computer);
				System.out.println(computer);	
			}
			
			protected abstract T addHardDisk(T hardDisk);
			protected abstract T addMotherBoard(T motherBoard);
			protected abstract T addKeyboard(T Keyboard);

		}
		
		public class DesktopManufacturer<T> extends ComputerManufacturer<T> {
			@SuppressWarnings("unchecked")
			@Override
			protected T addHardDisk(T hardDisk) {
				return (T) "H4 ";
			}

			@SuppressWarnings("unchecked")
			@Override
			protected T addMotherBoard(T motherBoard) {
				return (T) (motherBoard + ": M1: ");
			}

			@SuppressWarnings("unchecked")
			@Override
			protected T addKeyboard(T Keyboard) {
				return (T) (Keyboard + " : K2");
			}

		}
	
		public class LaptopManufacturer<T> extends ComputerManufacturer<T> {

			@SuppressWarnings("unchecked")
			@Override
			protected T addHardDisk(T hardDisk) {
				return (T) "H1 ";
			}

			@SuppressWarnings("unchecked")
			@Override
			protected T addMotherBoard(T motherBoard) {
				return (T) (motherBoard+ ": M2: ");
			}

			@SuppressWarnings("unchecked")
			@Override
			protected T addKeyboard(T Keyboard) {
				return (T) (Keyboard + " : k5");
			}
		}
		
		public class TestTemplateFactory {
			public static void main(String[] args) {
				ComputerManufacturer<String> cm = new DesktopManufacturer<>();
				cm.buildComputer();
			}
		}

	
