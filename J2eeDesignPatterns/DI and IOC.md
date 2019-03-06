# J2EE Design Patterns

##	Dependency Injection(DI)
	-	Instead of developer instanstiating an object 
	-	We will delegate the responsibility of creating and instanstiating object to container frameworks like Spring Framework
	-	We will achieve DI through IOC
	
	
##	Inversion of Control(IOC)
	-	Spring Container is a inversion of Control Container
	-	Since we are delegating the object creating from code to container ... this is called Inversion of Control

###	Create Spring Boot Application 

	-	Beans will be automatically managed by Spring Boot Application
	-	Stereo Type Components will created by Spring Container at runtime and will be injected dependent classes
	

	
## 	Code Snippet of DI and IOC

	Code Snippet:
		
		public interface CreditCard {
	
			void makePayment();
		}

		@Component
		class CreditCardImpl implements CreditCard {
			
			public void makePayment() {
				System.out.println("Payment Made Successfully");
			}
		}
		
		
		public interface Customer {
			void pay();
		}

		@Component
		class CustomerImpl implements Customer {
			
			@Autowired
			CreditCard card;

			public void pay() {
				card.makePayment();
			}
		}
	
##	Create Spring JUnit Test Class


	Code Snippet:
		
		@RunWith(SpringRunner.class)
		@SpringBootTest
		public class IocApplicationTests {
			
			@Autowired
			private Customer customer;

			@Test
			public void testPayment() {
				customer.pay();
			}

		}

		
##  Constructor Injection


	Code Snippet:
	
		@Component
		class CustomerImpl implements Customer {
			
			
			private CreditCard card;
			
			@Autowired
			private CustomerImpl(CreditCard card) {
				this.card = card;
			}

			public CreditCard getCard() {
				return card;
			}
			
			
			public void setCard(CreditCard card) {
				this.card = card;
			}

			public void pay() {
				card.makePayment();
			}
		}

		
## Setting Injection

	Code Snippet:
	
		@Component
		class CustomerImpl implements Customer {
			
			
			private CreditCard card;
			
			
			private CustomerImpl(CreditCard card) {
				this.card = card;
			}

			public CreditCard getCard() {
				return card;
			}
			
			@Autowired
			public void setCard(CreditCard card) {
				this.card = card;
			}

			public void pay() {
				card.makePayment();
			}
		}