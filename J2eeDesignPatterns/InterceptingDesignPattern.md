# Intercepting Filter Design Patterns

-	Intercepting Filter is used to do some special pre-processing on the incoming requests before it reaches the browser
-	Incoming requests will be handled by Request Handler
-	Sometimes we will intercept the incoming request and preprocess them
-	Some of the pre-processing tasks are:
	
	-	Authenticate
	-	Decompress
	-	Decode or Decrypt
	-	Audit
	
## Bad Browser Use Case

- 	Application can only be accessed from the chrome
-	If we use other type of browser then user will taken to badBrowser.jsp
-	Request will preprocessed by servlet filter
-	Filter will intercept the incoming request and will check the request header "User-Agent"
-	If Chrome then will redirect to HomeServlet in turn to home.jsp


	Code snippet:
	
		
		@WebServlet("/HomeServlet")
		public class HomeServlet extends HttpServlet {
			private static final long serialVersionUID = 1L;

			protected void doGet(HttpServletRequest request, HttpServletResponse response)
					throws ServletException, IOException {
				
				request.setAttribute("user","Bharath");
				RequestDispatcher requestDispatcher = request.getRequestDispatcher("home.jsp");
				requestDispatcher.forward(request, response);
			}
		}
		
		@WebFilter("/**")
		public class UserAgentFilter implements Filter {

			public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) throws IOException, ServletException {
				String header = ((HttpServletRequest )request).getHeader("User-Agent");
				System.out.println(header);
				if(header.contains("Chrome")) {
					chain.doFilter(request, response);
				} else {
					RequestDispatcher requestDispatcher = request.getRequestDispatcher("badBrowser.jsp");
					requestDispatcher.forward(request, response);
				}
				
			}
		}

		<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
			pageEncoding="ISO-8859-1"%>
		<!DOCTYPE html>
		<html>
		<head>
		<meta charset="ISO-8859-1">
		<title>Home</title>
		</head>
		<body>
		welcome <%= request.getAttribute("user") %>

		</body>
		</html>
		
-----------------------------------------------------------------		
		
		
		