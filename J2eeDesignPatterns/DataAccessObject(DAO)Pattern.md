# Data Access Object Pattern


-	DAO Pattern deals with CRUD Operation
-	DAO Pattern tells that all the DB operation should go to separate Class class DAO
-	That code can reuse across the project


## Creating DAO Pattern

-	Create an Interface for the Entity
-	Provide an implementation for that interface
-	Implementation class knows how to connect and perform CRUD operations


## Create a schema and table

-	Sql Queries

	Queries:

		show databases;
		use daodp;
		show tables;
		create table employee (id int, name varchar(10));
		select ** from employee;

		insert into employee values (1,'bharath');

## 	Data Access Object Simple Usecase


-	Create a Dao and Dao Impl class
-	Use Spring JDBC Template to Insert data into DB
-	Insert Data into DB
-	Run Spring JUnit Runner


## Implementation of Dao Pattern

	Code Snippets:

		Dao.java
		
		public interface Dao<T> {

			boolean create(T t);
		}

		IEmployeeDao.java
		
		public interface IEmployeeDao extends Dao<Employee> {
		}
		
		EmployeeImpl.java

		@Repository
		class EmployeeImpl implements IEmployeeDao {

			@Autowired
			JdbcTemplate template;
			
			@Override
			public boolean create(Employee employee) {
				String sql = "insert into employee values (?,?)";
				int rows = template.update(sql, employee.getId(), employee.getName());
				return rows > 0;
			}
		}
	
		
		Employee.java
		
		public class Employee {

			private int id;
			private String name;

			public int getId() {
				return id;
			}

			public void setId(int id) {
				this.id = id;
			}

			public String getName() {
				return name;
			}

			public void setName(String name) {
				this.name = name;
			}

		}
		
		application.properties
		
			spring.datasource.url=jdbc:mysql://localhost:3306/daodp
			spring.datasource.username=root
			spring.datasource.password=root

		DaoApplicationTests.java
		
		@RunWith(SpringRunner.class)
		@SpringBootTest
		public class DaoApplicationTests {

			@Autowired
			private IEmployeeDao dao;
			
			
			@Test
			public void createEmployee() {
				Employee e = new Employee();
				e.setId(2);
				e.setName("Guru");
				dao.create(e);
			}
		}
			
-----------------------------------------------------





































































































	