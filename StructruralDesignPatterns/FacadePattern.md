# Facade Pattern

-	Facade Design Pattern is one of the Structural design patterns (such as Adapter pattern and Decorator pattern)
-	Facade design pattern is used to help client applications to easily interact with the system

-	According to GoF Facade design pattern is:

	-	Provide a unified interface to a set of interfaces in a subsystem
	-	Facade Pattern defines a higher-level interface that makes the subsystem easier to use
	
## Facade Design Pattern Important Points

-	Facade design pattern is more like a helper for client applications
	-	It doesn’t hide subsystem interfaces from the client
	-	Whether to use Facade or not is completely dependent on client code
	
-	Facade design pattern can be applied at any point of development, usually when the number of interfaces grow and system gets complex
-	Subsystem interfaces are not aware of Facade and they shouldn’t have any reference of the Facade interface
-	Facade design pattern should be applied for similar kind of interfaces, its purpose is to provide a single interface rather than multiple interfaces that does the similar kind of jobs
-	We can use Factory pattern with Facade to provide better interface to client systems

## Use Cases for Facade Pattern

-	Suppose we have an application with set of interfaces to use MySql/Oracle database and to generate different types of reports, such as HTML report, PDF report etc....

	-	So we will have different set of interfaces to work with different types of database
	-	Now a client application can use these interfaces to get the required database connection and generate reports
	
-	Generating PDF and HTML  reports with firefox and chrome
-	Generating PDF and HTML reports with MySql and Oracle 

## Facade Pattern Implementation


	Code Snippet:
	
		public class MySqlHelper {
	
			public static Connection getMySqlDBConnection() {
				return null;
			}
			
			public void generateMySqlHTMLReport(Connection conn, String table) {
				System.out.println("Generating HTML report from MySql DB");
				
			}
			
			public void generateMySqlPDFReport(Connection conn, String table) {
				System.out.println("Generating PDF report from MySql DB");
			}

		}


		class OracleHelper {
			
			
			public static Connection getOracleDBConnection() {
				return null;
			}
			
			public void generateOracleHTMLReport(Connection conn, String table) {
				System.out.println("Generating HTML report from Oracle DB");
			}
			
			public void generateOraclePDFReport(Connection conn, String table) {
				System.out.println("Generating PDF report from Oracle DB");
			}

		}
		 

		public class HelperFacade {
	
			public static void gerenateReport(DBType db, ReportType report, String table) {
				
				Connection conn = null;
				
				switch(db) {
				case MYSQL:
					conn = MySqlHelper.getMySqlDBConnection();
					MySqlHelper mysqlHelper =  new MySqlHelper();
					switch(report) {
					case HTML:
						mysqlHelper.generateMySqlHTMLReport(conn, table);
						break;
					case PDF:
						mysqlHelper.generateMySqlPDFReport(conn, table);
						break;
					default:
						break;
					
					}
					break;
				case ORACLE:
					conn = OracleHelper.getOracleDBConnection();
					OracleHelper oracleHelper =  new OracleHelper();
					switch(report) {
					case HTML:
						oracleHelper.generateOracleHTMLReport(conn, table);
						break;
					case PDF:
						oracleHelper.generateOraclePDFReport(conn, table);
						break;
					default:
						break;
					
					}
					break;
				default:
					break;
				}
			}

			
			public static enum DBType {
				ORACLE, MYSQL
			}
			
			public static enum ReportType {
				PDF, HTML
			}
		}


			
		public class FacadeTest {
	
			public static void main(String[] args) {
				
				
				// Using Facade Helper to use the Subsystem
				HelperFacade.gerenateReport(DBType.MYSQL, ReportType.HTML, "table");
				HelperFacade.gerenateReport(DBType.MYSQL, ReportType.PDF, "table");
				HelperFacade.gerenateReport(DBType.ORACLE, ReportType.HTML, "table");
				HelperFacade.gerenateReport(DBType.ORACLE, ReportType.PDF, "table");
				
				
				// Without using facade pattern
				Connection conn = MySqlHelper.getMySqlDBConnection();
				MySqlHelper mHelper = new MySqlHelper();
				mHelper.generateMySqlHTMLReport(conn, "");
				mHelper.generateMySqlPDFReport(conn, "");
			}

		}

























































































