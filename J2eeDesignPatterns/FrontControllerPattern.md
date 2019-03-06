# Front Controller Design Pattern


-	Front Controller Design Pattern is used to handle to incoming request at one place centrally
-	If there is no Centralized Request Handler then view will end up with having business Processing and Navigation logic
-	If there is no Front Controller Pattern then view will have both business and navigation logic
	- This will result in two problems
		
		1.	Each view will have its own business logic and if there are any special processing like security ==> result in Code Duplication
		2.	View Navigation will be duplicated
		
-	View will became cumbersome to manage
-	This is Front Controller comes into picture


## Front Controller

-	Front Controller will handle all the incoming requests
- 	Front Controller will stand infront of the application and will manage the business logic and views separately
-	Front controller is responsible for taking the request and 	executing business logic and render the view

-	Front Controller has several components
	
	-	Client 
	-	Front Controller
	-	Command Helper
	-	Command
	-	Dispatcher 
	-	View 

-	Front Controller pattern solves the Business Processing logic and View Navigation Logic
-	Dispatcher servlet is the Front Controller in Spring Web Framework

