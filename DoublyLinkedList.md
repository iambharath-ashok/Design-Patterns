# Java Doubly LinkedList


-	Two Way LinkedList
-	Given a Node, we can navigate in both forward and backward direction which is not possible in Singly LinkedList
-	To delete a Node in Singly LinkedList, we needs to have a pointer to previous Node
-	But in Doubly LinkedList we can delete a Node, even if we don't have pointer to Previous Node
-	Doubly LinkedList has two pointers Head and Tail both points to extreme ends
-	Head Points to First Node and Tail Points to Last Node




		

## Representation of Doubly LinkedList

	public class Node<T> {
			
		private T data;
		private Node prev;
		private Node next;
		
		public Node(T data) {
			this.data = data;
		}
	}

	
	
	Code Snippet:
	
		public class DoublyLinkedList {
	
			private Node head;
			private Node tail;
			private int length;
			
			
			private static class Node {
				private int data; 
				private Node next;
				private Node previous;
				
				public Node(int data){
					this.data = data;
				}
			}
			
			
			public DoublyLinkedList() {
				head = null;
				tail = null;
				length = 0;
			}
			
			public int length() {
				return this.length;
			}
			
			public boolean isEmpty() {
				return this.length == 0;
			}
			
		}
		
## 	Inserting Elements at End

	Code Snippet:
	
		//Insert Element at end of Doubly LinkedList 
		public Node insertLast(int value) {
			Node newNode = new Node(value);
			if(this.isEmpty()) {
				this.head = newNode;
			} else {
				this.tail.next = newNode;
			} 
			newNode.previous = this.tail;
			this.tail = newNode;
			length ++;
			return this.head;
		}
		
## 	Print All the Elements of DL

	
	Code Snippet:
	
		public void displayForword() {
			if(this.isEmpty()) {
				System.out.println("List is Empty.");
				return;
			}
			
			Node temp = this.head;
			while(temp != null) {
				System.out.print(temp.data+"--->");
				temp = temp.next;
			}
			System.out.println("null");
		}
		
	Output:

		30--->40--->10--->20--->null
		
		
## 	Display in Backward Direction

	Code Snippet:

		//Display Backward Direction
		public void displayBackward() {
			
			if(this.isEmpty()) {
				System.out.println("List is Empty.");
				return;
			}
			Node temp = this.tail;
			while(temp!=null) {
				System.out.print(temp.data+"--->");
				temp = temp.previous;
			}
			System.out.println("null");
			
		}
		
	Output:
		
		90--->30--->40--->10--->20--->null
		20--->10--->40--->30--->90--->null



## 	Insert at Beginning of DLL


	Code Snippet:
		
		
		// Given Data insert at Beginning of DLL
		public void insertAtBeginning(int data) {
			Node newNode = new Node(data);
			if(this.isEmpty()) {
				this.tail = newNode;
			} else {
				head.previous = newNode;
			}
			newNode.next = head;
			head = newNode;
			length ++;
		}

	Output:
	
		30--->40--->10--->20--->null
		90--->30--->40--->10--->20--->null

## 	Insert at the End of DLL

	Code Snippet:
			
		// Given Data, insert at the End of DLL
		public void insertAtEnd(int data) {
			Node newNode = new Node(data);
			if(this.isEmpty()) {
				this.head = newNode;
			} else {
				this.tail.next = newNode;
			}
			newNode.previous = this.tail;
			this.tail = newNode;
			this.length ++;
			
		}
		
	Output:
				
		90--->30--->40--->10--->20--->null
		90--->30--->40--->10--->20--->80--->null	

## 	Delete Last Element of DLL

	Code Snippet:
			
		// Delete Last Element of DLL
		public void deleteLast() {
			if(this.isEmpty()) {
				System.out.println("List is Empty. Nothing to Delete.");
				return;
			}
			
			if(this.tail == this.head) {
				this.head = null;
			} else {
				this.tail.previous.next = null;
			}
			Node temp = this.tail;
			this.tail = this.tail.previous;
			temp = temp.next = temp.previous = null; 
		}
		
	Output:

		30--->40--->10--->20--->80--->null
		30--->40--->10--->20--->null



## 	Delete First Element of List

	Code Snippet:
		
		// Delete First Element of List
		public void deleteFirst() {
			if(this.isEmpty()) {
				System.out.println("List is Empty. Nothing to Delete.");
				return;
			}
			if(this.head == this.tail) {
				this.tail = null;
			} else {
				this.head.next.previous = null;
			}
			Node temp = this.head;
			this.head = this.head.next;
			temp = temp.next = temp.previous = null; 
		}		
	
	Output:
	
		90--->30--->40--->10--->20--->80--->null
		30--->40--->10--->20--->80--->null

## Full Program of DoublyLinkedList

	Code Snippet:
	
		package doublylinkedlist;

		public class DoublyLinkedList {
			
			private Node head;
			private Node tail;
			private int length;
			
			
			private static class Node {
				private int data; 
				private Node next;
				private Node previous;
				
				public Node(int data){
					this.data = data;
				}
			}
			
			
			public DoublyLinkedList() {
				head = null;
				tail = null;
				length = 0;
			}
			
			public int length() {
				return this.length;
			}
			
			public boolean isEmpty() {
				return this.length == 0;
			}
			
			//Insert Element at end of Doubly LinkedList 
			public void insertLast(int value) {
				Node newNode = new Node(value);
				if(this.isEmpty()) {
					this.head = newNode;
				} else {
					this.tail.next = newNode;
				} 
				newNode.previous = this.tail;
				this.tail = newNode;
				length ++;
			}
			
			//Display List in Forward Direction
			public void displayForword() {
				if(this.isEmpty()) {
					System.out.println("List is Empty.");
					return;
				}
				Node temp = this.head;
				while(temp != null) {
					System.out.print(temp.data+"--->");
					temp = temp.next;
				}
				System.out.println("null");
			}
			
			//Display Backward Direction
			public void displayBackward() {
				
				if(this.isEmpty()) {
					System.out.println("List is Empty.");
					return;
				}
				Node temp = this.tail;
				while(temp!=null) {
					System.out.print(temp.data+"--->");
					temp = temp.previous;
				}
				System.out.println("null");
				
			}
			
			// Given Data insert at Biginning of DLL
			public void insertAtBeginning(int data) {
				Node newNode = new Node(data);
				if(this.isEmpty()) {
					this.tail = newNode;
				} else {
					head.previous = newNode;
				}
				newNode.next = head;
				head = newNode;
				length ++;
			}
			
			// Given Data, insert at of DLL
			public void insertAtEnd(int data) {
				Node newNode = new Node(data);
				if(this.isEmpty()) {
					this.head = newNode;
				} else {
					this.tail.next = newNode;
				}
				newNode.previous = this.tail;
				this.tail = newNode;
				this.length ++;
				
			}
			
			// Delete Last Element of DLL
			public void deleteLast() {
				if(this.isEmpty()) {
					System.out.println("List is Empty. Nothing to Delete.");
					return;
				}
				
				if(this.tail == this.head) {
					this.head = null;
				} else {
					this.tail.previous.next = null;
				}
				Node temp = this.tail;
				this.tail = this.tail.previous;
				temp = temp.next = temp.previous = null; 
			}
			
			// Delete First Element of List
			public void deleteFirst() {
				if(this.isEmpty()) {
					System.out.println("List is Empty. Nothing to Delete.");
					return;
				}
				if(this.head == this.tail) {
					this.tail = null;
				} else {
					this.head.next.previous = null;
				}
				Node temp = this.head;
				this.head = this.head.next;
				temp = temp.next = temp.previous = null; 
			}
			
			
			
			public static void main(String[] args) {
				DoublyLinkedList dll = new DoublyLinkedList();
				dll.insertLast(30);
				dll.insertLast(40);
				dll.insertLast(10);
				dll.insertLast(20);
				dll.displayForword();
				dll.insertAtBeginning(90);
				dll.displayForword();
				dll.displayBackward();
				dll.insertAtEnd(80);
				dll.displayForword();
				dll.deleteFirst();
				dll.displayForword();
				dll.deleteLast();
				dll.displayForword();
			}
			
		}















































 



