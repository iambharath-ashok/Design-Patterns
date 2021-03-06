## Guru Raghavendra Vaibhava 

## Java Design Patterns


## What are Design Patterns?

- 	Identify Recurring problems 
-	Provide ready to use solutions
-	Three imp terms: Problem, solution, Context

## Gang of Four Pattern

-	4 Guys have  written a book called Elements of Reusable Object Oriented S/w


## Why Design Patterns?

-	Capture Design Experience
-	Promote reuse without having to reinvent the wheel
-	Define the system structure better
-	Provide a common design language

## Pattern Identification

-	When we encounter with problem: 
	-	We will check whether is solution is already available, if there we will reuse them
	-	If there are solutions already available:
		-	We will document the problem with the solution following a pattern template
		-	Initially it will called as candidate pattern
	
	-	If Problem is recurring applications or across different projects
	-	We will check whether candidate pattern solves the issue
	-	If it solves,then solution will be written to Pattern catalog
	-	Then candidate pattern will become design pattern
	
## Pattern Catalog

-	 Based the problem that pattern solves, Patterns are divided into multiple categories
-	There 2 types of patterns :

	-	Core Pattern or Gang of Four Pattern
	-	JEE Pattern for Enterprise applications
	
	-	Core Pattern is divided into
		
		-	Creational Pattern
			-	Deals with Object Creation
				-	Factory 
				-	Singleton
				-	Abstract Factory
				-	Builder 
				-	Prototype
				
		-	Structural Pattern
			-	Deals with relationship b/w Classes
				
				-	Adapter
				-	Bridge
				-	Flyweight
				-	Decorator
				-	Proxy
				
				
		-	Behavioral Pattern
			-	Deals with communication b/w Objects and Classes
	
				-	Command 
				- 	Interpreter
				-	Template Method
				-	Observer
	
## JEE Pattern Catalog

-	Every Java application is logically divided into multiple layers
	-	Presentation Layer
	-	Business Layer
	-	Service Layer
	-	Integration Layer
	-	Data Access Layer
-	JEE Patterns are categorized based on these layers

	-	Presentation Layer
		
		-	Front Controller
		-	Intercepting Filter
		-	MVC
		-	Context Object
		
	-	Business Layer
		
		-	Business Delegate
		-	Transfer Object
		-	Session Facade
		- 	Service Locater
		
	-	Data Access Layer
		
		-	Data Access Object Pattern
	
	- 	Integration Layer
	
		-	Service Activator


---------------------------------------------------------
## Singleton Pattern

-	Examples of Singleton Pattern
-	Property Reader Object
	-	Only one Object will be created per application
	-	Consumes more memory
	-	All properties will be read from Property file instantiated into PropertyReader Instance
	
-	Logger:
	-	debug, error, info
	-	Same Logger instance will shared across all the application classes
	
-	Datasource Class from JDBC
	-	Datasource maintains the connection pool 
	-	Datasource provides connection whenever connection is required by diff classes 
	
	
-	Singleton Uml Diagram

	
-	Singleton Lazy and Early Initialization with Thread Safety
		
	Code Snippet Of Early Initialization:
	
		public class DateUtil {
			private static DateUtil du;
			private DateUtil() {
				
			}
			
			public static DateUtil getInstance() {
				if(du == null) {
					synchronized(DateUtil.class) {
						if(du == null) {
							du = new DateUtil();
						}
					}
				}
				return du;
			}
		}


	Code Snippet Of Lazy Initialization:

		public class DateUtil {

			private static DateUtil du = new DateUtil();

			private DateUtil() {
			}

			public static DateUtil getInstance() {
				return du;
			}
		}
	
	

-	Singleton with Serialization
	
	Code Snippet of Serialization:
	
		public class DateUtil implements Serializable, Cloneable {

			
			private static final long serialVersionUID = 1L;
			private static DateUtil INSTANCE = getInstance();

			private DateUtil() {
			}

			public static DateUtil getInstance() {
				if (INSTANCE == null) {
					synchronized (DateUtil.class) {
						if (INSTANCE == null) {
							INSTANCE = new DateUtil();
						}
					}
				}
				return INSTANCE;
			}

			protected Object readResolve() {
				return INSTANCE;
			}
		}
		
-	Singleton with cloning
	
	
	Code Snippet:
	
		package singleton;

		import java.io.Serializable;

		public class DateUtil implements Serializable, Cloneable {

		
			private static final long serialVersionUID = 1L;
			private static DateUtil INSTANCE = getInstance();

			private DateUtil() {
			}

			public static DateUtil getInstance() {
				if (INSTANCE == null) {
					synchronized (DateUtil.class) {
						if (INSTANCE == null) {
							INSTANCE = new DateUtil();
						}
					}
				}
				return INSTANCE;
			}

			protected Object readResolve() {
				return INSTANCE;
			}

			protected Object clone() throws CloneNotSupportedException {
				throw new CloneNotSupportedException();
			}
		}
		
-	Singleton Logger Implementation:

		code snippet:
		
			package singleton;

			import java.io.Serializable;

			public final class Logger implements Cloneable, Serializable {

				private static final long serialVersionUID = 1L;
				public volatile static Logger instance = getInstance();

				private Logger() {

				}

				public static Logger getInstance() {
					if (instance == null) {
						synchronized (Logger.class) {
							if (instance == null) {
								instance = new Logger();
							}
						}
					}
					return instance;
				}

				public void log(String message) {
					System.out.println(message);
				}

				public Object clone() throws CloneNotSupportedException {
					throw new CloneNotSupportedException();
				}
				
				public Object readResolve() {
					return instance;
				}
				
			}

----------------------------------------------------------------

	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	



	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	




	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	



