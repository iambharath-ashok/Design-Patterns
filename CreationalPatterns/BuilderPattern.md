# Builder Pattern

-	Builder pattern was introduced to solve some of the problems with Factory and Abstract Factory design patterns
-	When the Object contains a lot of attributes
-	There are three major issues with Factory and Abstract Factory design patterns when the Object contains a lot of attributes	

	-	Too Many arguments to pass from client program to the Factory class, its hard to maintain the order of the argument
	-	Some of the parameters might be optional but in Factory pattern, we are forced to send all the parameters and optional parameters need to send as NULL
	-	If the object is heavy and its creation is complex, then all that complexity will be part of Factory classes that is confusing
	
	
	
-	Builder pattern solves the issue with large number of optional parameters and inconsistent state 
-	By providing a way to build the object step-by-step and provide a method that will actually return the final Object	

	
## Examples of Builder Pattern

-	Account with Address and Name
-	Vehicle with engine and wheel optional as airbags
-	Computer with mother board, ram, hdd and option graphics card as optional
		

## Implementation example of Builder Pattern


	Code Snippet:
	
		package builder;

		public class TestBuilder {

			public static void main(String[] args) {

				Account account = new Account.AccountBuilder().build();
				System.out.println(account);
				
				account = new Account.AccountBuilder().id(1).email("bharath.ashok@gmail.com").build();
				System.out.println(account);
				
				Name name = new Name.NameBuilder().firstName("bharath").lastName("ashok").surName("The Great").build();
				account = new Account.AccountBuilder().name(name).id(1).email("bharath.ashok@ymail.com").build();
				System.out.println(account);
			}
		}

		Account.java
		
		
		package builder;

		public class Account {

			private final int id;
			private final String email;
			private final Address address;
			private final Name name;

			private Account(AccountBuilder builder) {
				this.id = builder.id;
				this.email = builder.email;
				this.address = builder.address;
				this.name = builder.name;
			}

			public static class AccountBuilder {

				private int id;
				private String email;
				private Address address;
				private Name name;

				public AccountBuilder id(int id) {
					this.id = id;
					return this;
				}

				public AccountBuilder email(String email) {
					this.email = email;
					return this;
				}

				public AccountBuilder address(Address address) {
					this.address = address;
					return this;
				}

				public AccountBuilder name(Name name) {
					this.name = name;
					return this;
				}

				public Account build() {
					return new Account(this);
				}

			}

			public int getId() {
				return id;
			}

			public String getEmail() {
				return email;
			}

			public Address getAddress() {
				return address;
			}

			public Name getName() {
				return name;
			}

			@Override
			public String toString() {
				return "Account [id=" + id + ", email=" + email + ", address=" + address + ", name=" + name + "]";
			}

		}
		
		
		Address.java

		package builder;

		public class Address {

			private final String street;
			private final int zipcode;
			private final String city;

			private Address(AddressBuilder builder) {
				this.street = builder.street;
				this.zipcode = builder.zipcode;
				this.city = builder.city;
			}

			public static class AddressBuilder {
				private String street;
				private int zipcode;
				private String city;

				public AddressBuilder street(String street) {
					this.street = street;
					return this;
				}

				public AddressBuilder zipcode(int zipcode) {
					this.zipcode = zipcode;
					return this;
				}

				public AddressBuilder city(String city) {
					this.city = city;
					return this;
				}

				public Address build() {
					return new Address(this);
				}
			}

			public String getStreet() {
				return street;
			}

			public int getZipcode() {
				return zipcode;
			}

			public String getCity() {
				return city;
			}

			@Override
			public String toString() {
				return "Address [street=" + street + ", zipcode=" + zipcode + ", city=" + city + "]";
			}

		}
		
		
		Name.java
		
		
		package builder;

		public class Name {

			private final String firstName;
			private final String lastName;
			private final String middleName;
			private final String surName;

			private Name(NameBuilder builder) {
				this.firstName = builder.firstName;
				this.lastName = builder.lastName;
				this.middleName = builder.middleName;
				this.surName = builder.surName;
			}

			public static class NameBuilder {

				private String firstName;
				private String lastName;
				private String middleName;
				private String surName;

				public NameBuilder firstName(String firstName) {
					this.firstName = firstName;
					return this;
				}

				public NameBuilder lastName(String lastName) {
					this.lastName = lastName;
					return this;
				}

				public NameBuilder middleName(String middleName) {
					this.middleName = middleName;
					return this;
				}

				public NameBuilder surName(String surName) {
					this.surName = surName;
					return this;
				}

				public Name build() {
					return new Name(this);
				}
			}

			public String getFirstName() {
				return firstName;
			}

			@Override
			public String toString() {
				return "Name [firstName=" + firstName + ", lastName=" + lastName + ", middleName=" + middleName + ", surName="
						+ surName + "]";
			}

			public String getLastName() {
				return lastName;
			}

			public String getMiddleName() {
				return middleName;
			}

			public String getSurName() {
				return surName;
			}
		}
