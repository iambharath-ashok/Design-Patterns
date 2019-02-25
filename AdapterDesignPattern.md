# Adapter Pattern

-	Adapter Pattern is Structural Pattern
-	Adapter Pattern is similar to Power Adapter 
-	Power Adapter will adapt to local switch or local
-	In programming world when two application are communicating with each other, then we may need to adapt at some places
-	EX: Whether Application with Adapter


## UML Diagram of Adapter Pattern

## Implementation of Adapter Pattern
	
	Code Snippet:
	
		package adapter;

		public interface WhetherFinder {

			public int find(String city);
		}
		
		public class WetherFinderImpl implements WhetherFinder {

			@Override
			public int find(String city) {
				int temp = 0;
				switch(city) {
				case "bengaluru":
					temp = 28;
					break;
				case "new delhi":
					temp = 24;
					break;
				}
				return temp;
			}
		}	
		
		public class WhetherIUI {
			public int showTemperatur(int zipcode) {
				WhetherAdapter wa = new WhetherAdapter();
				int temp = wa.findTemperature(zipcode);
				return temp;
			}
		}


		public class WhetherAdapter {
			public int findTemperature(int zipcode) {
				String city = "";
				if(zipcode == 56001) {
					city = "bengaluru";
				} else if(zipcode == 10001) {
					city = "new delhi";
				}
				WhetherFinder wf = new WetherFinderImpl();
				int temp = wf.find(city);
				return temp;
			}
		}
		
		public class TestAdapterDP {
			public static void main(String[] args) {
				WhetherIUI ui = new WhetherIUI();
				int temp = ui.showTemperatur(56001);
				System.out.println(temp);
			}
		}

## Adapter Design Pattern of Payment Processor


	Code Snippet:
	
		package adapter.paymentprocessor;
		
		public interface PaymentProcessor {

			boolean pay(int dollors);
		}

		public class PaymentProcessorImpl implements PaymentProcessor {

			@Override
			public boolean pay(int dollars) {
				System.out.println("$"+ dollars +" has been paid");
				return Boolean.TRUE;
			}
		}
		
		public class PaymentApp {
			public boolean makePayment(int rupees) {
				PaymentAdapter pa = new PaymentAdapter();
				boolean isSuccess = pa.payAmount(rupees);
				return isSuccess;
			}
		}

		
		public class PaymentAdapter {
			public boolean payAmount(int rupees) {
				int currentAmount = 71;
				PaymentProcessor pp = new PaymentProcessorImpl();
				boolean isSuccess = pp.pay(rupees / currentAmount);
				return isSuccess;
			}
		}
	
	
		public class TestPaymentAdaptor {
			public static void main(String[] args) {
				PaymentApp app = new PaymentApp();
				app.makePayment(790);
			}
		}

	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	