# Movie Ticket Use Case

-	For each customer a ticket will created and save in the DB

## Business Delegate Pattern 

-	Business Delegate Pattern is used to achieve loose coupling b/w Presentation layer and DAO Layer
-	Business Delegate Pattern helps is code resuability


## Business Object Pattern

- 	Business Object is similar to DB Entity class
-	BO is used to achive loose coupling b/w presentation and DB	

## Code Snippet 

	public interface Dao<T> {
	
		boolean create(T t);
	}
	
	
	public interface ITicketDao extends Dao<Ticket>{

	}

	@Repository
	class TicketDaoImpl implements ITicketDao {
		
		@Autowired
		private JdbcTemplate jdbcTemplate;
		
		@Override
		public boolean create(Ticket ticket) {
			String sql = "insert into ticket(movie, screen, seat) values(?,?,?)";
			int rows = jdbcTemplate.update(sql, ticket.getMovie(), ticket.getScreen(), ticket.getSeat());
			return rows > 0;
		}
		
	}

		public class Ticket {

			private String movie;
			private String screen;
			private String seat;

			public String getMovie() {
				return movie;
			}

			public void setMovie(String movie) {
				this.movie = movie;
			}

			public String getScreen() {
				return screen;
			}

			public void setScreen(String screen) {
				this.screen = screen;
			}

			public String getSeat() {
				return seat;
			}

			public void setSeat(String seat) {
				this.seat = seat;
			}

		}

		public interface IPurchaseTicketService {

			boolean purchaseTicket(Ticket ticket);
		}

		@Service
		class PuchaseTicketServiceImpl implements IPurchaseTicketService {

			@Autowired
			private ITicketDao ticketDao;

			@Override
			public boolean purchaseTicket(Ticket ticket) {
				return ticketDao.create(ticket);
			}

		}
		
		@Controller
		public class TicketController {

			@Autowired
			private IPurchaseTicketService ticketService;

			@RequestMapping("showCreateTicket")
			public String showCreateTicket() {
				return "createMovieTicket";
			}

			@RequestMapping(path="createMovieTicket.do", method = RequestMethod.POST)
			public String createMovieCreate(Ticket ticket, ModelMap map) {
				if (ticketService.purchaseTicket(ticket))
					map.addAttribute("msg", "Movie Ticket Purchase successful.");
				else
					map.addAttribute("msg", "Movie Ticket Purchase failed.");
				return "createMovieTicket";
			}

		}
		


		application.properties

			spring.mvc.view.prefix=/WEB-INF/views/
			spring.mvc.view.suffix=.jsp


			server.servlet.context-path=/movietickets

			spring.datasource.url=jdbc:mysql://localhost:3306/movieticket
			spring.datasource.username=root
			spring.datasource.password=root
			
			
		createMovieTicket.jsp


			<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
				pageEncoding="ISO-8859-1"%>
			<!DOCTYPE html>
			<html>
			<head>
			<meta charset="ISO-8859-1">
			<title>Purchase Movie Ticket</title>
			</head>
			<body>
				<form method = "post" action="createMovieTicket.do">
					Movie Name: <input type="text" name = "movie"/> <br/>
					Screen: <input type ="text" name= "screen"/> <br/>
					Seat: <input type = "text" name = "seat"/> <br/>
					<input type="submit" value="purchase ticket">
				</form>
				${msg}
			</body>
			</html>
			
			
		sql

			create schema movieticket;
			use movieticket;
			show tables;

			create table ticket
			(
			id int not null Auto_Increment,
			movie varchar(20),
			screen varchar(20),
			seat varchar(20),
			primary key(id)
			);

			select * from ticket;