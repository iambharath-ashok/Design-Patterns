# MVC Pattern

-	MVC is a Design Pattern or Framework that splits the web layer into 3 parts
-	Model 
	- 	Which represents the current state of the application
	-	Model will be used in processing business logic
	-	Model will interact with DB
	
-	View Layer

	-	A view representation of Model will send to end user
	-	View can be JSP or html 
	
-	Controller 

	-	Controller acts as glue b/w View and Model
	-	When an request comes, container will select appropriate controller and controller will in-turn choose the appropriate Model
	-	Model after processing business logic, will return a appropriate view to Controller
	-	Controller will choose the view and send that dispatcher servlet
-----------------------------------------------------------------	
	
## Advantages of using MVC Pattern

-	Maintenance
-	Parallel Development
-----------------------------------------------------------------

## In Jsp and Servlet World

-	Servlet will controller
-	View will represented by Jsp
-	Model will be represented by Java Class 	

-----------------------------------------------------------------
## Model View Controller with Dynamic Web Project and Servlet as Controller
	
	Steps:
	
		-	Create Dynamic Web Project 
		-	Create a View
		-	Create a Controller
		-	Create a Model

	Code Snippet:
		
		average.html

		<!DOCTYPE html>
		<html>
		<head>
		<meta charset="ISO-8859-1">
		<title>Average of Two Numbers</title>
		</head>
		<body>

			<form method = "post" action ="averageController.do">
				Number 1 : <input type ="number" name= "number1"> <br/>
				Number 2 : <input type ="number" name="number2"> <br/>
				<input type="submit"/>
			</form>

		</body>
		</html>
	
		
		AverageModel.java
		
		public class AverageModel {
			public int  findAverage(int number1 , int number2) {
				return (number1 + number2) /2;
			}
		}
	
	
		AverageController.java
		
		@WebServlet("*.do")
		public class AverageController extends HttpServlet {
			private static final long serialVersionUID = 1L;

			protected void doPost(HttpServletRequest request, HttpServletResponse response)
					throws ServletException, IOException {

				int number1 = Integer.parseInt(request.getParameter("number1"));
				int number2 = Integer.parseInt(request.getParameter("number2"));
				
				AverageModel am = new AverageModel();
				int average = am.findAverage(number1, number2);
				
				request.setAttribute("average", average);
				
				RequestDispatcher  rd = request.getRequestDispatcher("result.jsp");
				rd.forward(request, response);
			}
		}

		
		result.jsp
		
		<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
			pageEncoding="ISO-8859-1"%>
		<!DOCTYPE html>
		<html>
		<head>
		<meta charset="ISO-8859-1">
		<title>Result of Average of Two Numbers</title>
		</head>
		<body>
			<%
				String average = String.valueOf(request.getAttribute("average"));
				out.println("The average of two number is: "+ average);
			%>
		</body>
		</html>
-----------------------------------------------------------------

## Model View Controller with Spring Boot


	Steps:
	
		-	Create Spring Boot Application
		-	Create a Model
		-	Create a Controller
		-	Create a View
		-	Add embedded Jasper dependency to serve Jsp's from the jar
		
		
		
		
	Code Snippet:
	
		helloMvc.jsp
		
			<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
				pageEncoding="ISO-8859-1"%>
			<!DOCTYPE html>
			<html>
			<head>
			<meta charset="ISO-8859-1">
			<title>Hello</title>
			</head>
			<body>
			<h3>Hello <%= request.getAttribute("userName") %></h3>
			<br/>
			<a href="calculateGreatest.do">Find Greatest of Two Numbers</a>
			</body>
			</html>
	
	
		HelloController.java
		
			@Controller
			public class GreatestOfTwoController {

				@RequestMapping(path = "calculateGreatest.do", method = RequestMethod.POST)
				public String findGreatest(int number1, int number2, Model model) {
					GreatestModel gm = new GreatestModel();
					int greatest = gm.findGreatest(number1, number2);
					model.addAttribute("greatest", greatest);
					return "result";
				}
				
				@RequestMapping(path = "calculateGreatest.do", method = RequestMethod.GET)
				public String findGreatest() {
					return "findGreatest";
				}
			}

	
		findGreatest.jsp
		
			<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
				pageEncoding="ISO-8859-1"%>
			<!DOCTYPE html>
			<html>
			<head>
			<meta charset="ISO-8859-1">
			<title>Find Greatest of Two Numbers</title>
			</head>
			<body>

				<form method = "post" action ="calculateGreatest.do">
					Number1 : <input type="number" name= "number1"> <br/>
					Number2 : <input type="number" name= "number2"> <br/>
					<input type="Submit" name="Find Greatest" >
				</form>

			</body>
			</html>
			
			
		GreatestOfTwoController.java
		
			@Controller
			public class GreatestOfTwoController {

				@RequestMapping(path = "calculateGreatest.do", method = RequestMethod.POST)
				public String findGreatest(int number1, int number2, Model model) {
					GreatestModel gm = new GreatestModel();
					int greatest = gm.findGreatest(number1, number2);
					model.addAttribute("greatest", greatest);
					return "result";
				}
				
				@RequestMapping(path = "calculateGreatest.do", method = RequestMethod.GET)
				public String findGreatest() {
					return "findGreatest";
				}
			}

	
	
		GreatestModel.java
		
			public class GreatestModel {
		
				public int findGreatest(int number1,int number2) {
					return number1 > number2 ? number1 : number2;
				}

			}
	
		result.jsp
		
			<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
			pageEncoding="ISO-8859-1"%>
			<!DOCTYPE html>
			<html>
			<head>
			<meta charset="ISO-8859-1">
			<title>Result</title>
			</head>
			<body>

			<% 
				String greatest = String.valueOf(request.getAttribute("greatest"));
				out.println("The Greatest of Two Numbers is: " + greatest);
			%>

			</body>
			</html>
		
	
		application.properties
		
		
			spring.mvc.view.suffix=.jsp
			spring.mvc.view.prefix=/WEB-INF/jsps/
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	



	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	



	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	



	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	



	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	



	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	


