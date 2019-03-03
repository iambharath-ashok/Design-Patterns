# Proxy Pattern

-	Proxy Design pattern is one of the Structural design pattern and is one of the simplest pattern
-	Proxy design pattern intent according to GoF is:

	-	Provide a surrogate or placeholder for another object to control access to it
	
-	Proxy design pattern is used when we want to provide controlled access of a functionality


## Proxy Pattern Implementation

	Code Snippet:
	
		
		package proxy;

		public interface DatabaseExecutor {

			void executeDatabase(String query);
		}

		class DatabaseExecutorImpl implements DatabaseExecutor {

			@Override
			public void executeDatabase(String query) {
				System.out.println("Executing Query: " + query);
			}
		}

		class DatabaseExecutorProxy implements DatabaseExecutor {
			private boolean isAdmin;
			private DatabaseExecutor executor;

			public DatabaseExecutorProxy(String user, String password) {
				if (user.equalsIgnoreCase("admin") && password.equals("1234"))
					isAdmin = true;
				executor = new DatabaseExecutorImpl();
			}

			@Override
			public void executeDatabase(String query) {
				if(this.isAdmin) {
					executor.executeDatabase(query);
				} else {
					if(query.contains("delete")) {
						throw new IllegalAccessError("Delete is not supported");
					}
					executor.executeDatabase(query);
				}
			}
		}

		public class ProxyTest {
	
			public static void main(String[] args) {
				
				DatabaseExecutor exec = new DatabaseExecutorProxy("admin","1234");
				exec.executeDatabase("delete from table");
				
				exec = new DatabaseExecutorProxy("user1","delete");
				exec.executeDatabase("delete from table");
			}
		}