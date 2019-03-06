# JEE Application Layers and Classes

-	Each Jee application is divided in two different layers

-	Data Access Layers
-	Services/Business Layers
-	Integration Layers
-	Presentation Layers

## Data Access Layers

-	Data Access Layer is a independent layer
-	Data Access Layer is responsible for CRUD operation against Data source like DB


## Services/Business Layer

-	This layer consists of business logic and services
-	Services provided by services layers will be used by presentation and integration layers
-	Services layer will interact with Data access layer 

##	Integration Layer

-	Integration Layer will interact with external services or other applications or third party applications
-	Integration Layer will provide services to external sources
-	Integration Layer will Consume Services from Services/Business Layer

## Presentation Layer 

-	Presentation Layer deals with UI will interact with Services/Business Layer
-	Controller Layer is responsible for interact with services layer and generating UI for the application
-----------------------------------------------------------------------
## Classes and Interfaces

-	All Layer of Jee application is made up of Classes and Interfaces
-	There 10 classes or Interfaces or 9 + 1 classes or Interfaces


	1.	Model class or Domain class (c) 
	
		- 	This is usually used on all the layers of the application
		-	This is a Transfer Object b/w the layers
	
	2.	Utility Classes (C)
	
		-	Logic that needs to be reused across the layers are used in Utility class
		-	Utility classes are used across the layers

	3.	Validator Classes (C)

		-	Validator classes are used for validating the data that comes in and goes out
		-	Will be used across the layers
		
	4. View (C)

		-	It's a special class used for generating the view like PDF, Excell Sheet
		
		
###	Presentation Layer

-	Controller (C)
	
	-	Responsible for generating view and interacting with services layer
	
### Service Layer

-	IService (I)
-	IServiceImpl (C)
	
	-	Consumer service from Data Access Layer
	
### Data Access Layer

-	IDao(I)
-	DAOImpl (C)
	-	performs CRUD operations 
	
### Integration Layers

-	This is consists of Webservice classes that provides services or consumer the services

-----------------------------------------------------------------------
## Why Layer Architecture

-	Simplicity
-	Seperation of Concerns
-	Easy Maintenance

------------------------------------------------------------
## Design Patterns on each layer of Jee 

-	Interceptor filter
-	Front Controller
-	MVC
-	Business Delegate
-	Business Object
-	Data Access Object

------------------------------------------------------------



































