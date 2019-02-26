# Command Pattern

-	Command Pattern is Behavioral Pattern
-	In Command Pattern, request will be encapsulated into an Object and passed to invoker
-	Invoker doesn't know how to serve the request it use the command to pass the request to receiver
-	Receiver knows how to service the request
-	There are 5 Actors in the Command Pattern

	1.	Client
	2.	Invoker
	3.	Command
	4.	Concrete Command
	5.	Receiver
	
	
-	Ex: Person using Remote to Switch off and on the television
-	Person is the client
-	Remote the invoker
-	Commands are OnCommand and OffCommand 
-	Major Advantage of Command Pattern is that, Invoker and Receiver


## UML Diagram

## Command Pattern Impl

	Code Snippet:
	
		package command;

		public interface Command {
			void execute();
		}

		class OnCommand implements Command {

			private Television television;
			public OnCommand(Television television) {
				this.television = television;
			}

			public void execute() {
				this.television.on();
			}
		}

		class OffCommand implements Command {

			private Television television;
			public OffCommand(Television television) {
				this.television = television;
			}

			public void execute() {
				this.television.off();
			}
		}
		
		
		public class RemoteController {

			private Command command;
			public Command getCommand() {
				return command;
			}

			public void setCommand(Command command) {
				this.command = command;
			}

			public void pressButton() {
				this.command.execute();
			}
		}
		
		
		public class Television {

			public boolean on() {
				System.out.println("Television switch on");
				return true;
			}

			public boolean off() {
				System.out.println("Television switched off");
				return true;
			}
		}
	
		
		public class Person {

			public static void main(String[] args) {
				Television television = new Television();
				RemoteController remote = new RemoteController();
				OnCommand on = new OnCommand(television);
				remote.setCommand(on);
				remote.pressButton();
				
				remote.setCommand(new OffCommand(television));
				remote.pressButton();
			}
		}
