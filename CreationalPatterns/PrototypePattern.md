# Prototype Pattern

-	Prototype design pattern is used when the Object creation is a costly affair 
-	And requires a lot of time and resources and we have a similar object already existing
-	Prototype pattern provides a mechanism to copy the original object to a new object 
-	And then modify it according to our needs
- 	Prototype design pattern uses Java cloning to copy the object
-----------------------------------------------------------------
## Prototype Design Pattern Example

-	Suppose we have an Object that loads data from database
-	Now we need to modify this data in our program multiple times
-	So it’s not a good idea to create the Object using new keyword and load all the data again from database
-----------------------------------------------------------------

## Prototype Points 

-	Object will be created from already existing object
-	Prototype Pattern use Java Cloneable and deep copy

-----------------------------------------------------------------
## Cloning in Java

-	Any Java class that needs to be clone, should provide a permission of cloning by implementing cloneable interface
-	Cloneable in a marker interface that doesn't have any methods in it

-	Clone method is declared in Object class and is protected .... 
	-	So in order to clone, we needs to override the clone method in the child class
	
-	There are two type of cloning in Java i.e... Shallow and Deep Cloning
- 	Shallow Cloning:

	-	Shallow Cloning ... Same Object will pointing by two different reference
	-	Changes made with one reference will be reflected in other reference
	
-	Deep Cloning:

	-	In deep Cloning ... Two different Objects will created and referenced by two diff references
	-	Changes made to objects will not be reflect with each other
-----------------------------------------------------------------	
##  Prototype Pattern implementation


	Code Snippet:
	
		public class Book {

			private int id;
			private String bookName;

			public int getId() {
				return id;
			}

			public void setId(int id) {
				this.id = id;
			}

			public String getBookName() {
				return bookName;
			}

			public void setBookName(String bookName) {
				this.bookName = bookName;
			}

			@Override
			public String toString() {
				return "Book [id=" + id + ", bookName=" + bookName + "]";
			}

		}
	
		public class BookShop implements Cloneable {

			private String shopName;
			private List<Book> books = new ArrayList<>();

			public String getShopName() {
				return shopName;
			}

			public void setShopName(String shopName) {
				this.shopName = shopName;
			}

			public List<Book> getBooks() {
				return books;
			}

			public void setBooks(List<Book> books) {
				this.books = books;
			}

			@Override
			public String toString() {
				return "BookShop [shopName=" + shopName + ", books=" + books + "]";
			}
			
			
			public void loadData() {
				for (int i = 1; i <=10; i++) {
					Book b = new Book();
					b.setBookName("Book "+ i);
					b.setId(i);
					this.getBooks().add(b);
				}
			}
			
			@Override
			public BookShop clone() throws CloneNotSupportedException {
				BookShop bs = new BookShop();
				for(Book b : this.getBooks()) {
					bs.getBooks().add(b);
				}
				return bs;
			}
		}

		public class TestPrototypePattern {
			public static void main(String[] args) throws CloneNotSupportedException {

				BookShop bs = new BookShop();
				bs.setShopName("Shop 1");
				bs.loadData();
				System.out.println(bs);
				System.out.println("==================================");
				BookShop bs2 = bs.clone();
				bs2.setShopName("Shop 2");
				bs.getBooks().remove(1);
				System.out.println(bs2);
				System.out.println(bs);
			}
		}
	
-----------------------------------------------------------------
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	


