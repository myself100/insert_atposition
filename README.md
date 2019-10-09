# insert_atposition

package elclipse;
import java.util.*;
public class InsertAtposition {

	public static class ListNode{
		private int data;
		private ListNode next;

		public ListNode(int data) {
			this.data=data;
			this.next=null;
		}
	}

	public static int total(ListNode head) {
		int count=1;
		if(head==null) {
			return -1;
		}
		ListNode current=head;
		while(current!=null) {
			current = current.next;
			count++;
		}
		return count;
	}

	public ListNode insertatposition(ListNode head,int data,int position) {
		ListNode newNode= new ListNode(data);
		int size=total(head);
		if(position > size+1 || position<1) {
			System.out.print("Invalid position");
			return head;
		}
		if(position==1) {
			newNode.next=head;
			return newNode;
		}
		else {
			ListNode previous=head;
			int count=1;
			while(count<position-1) {
				previous=previous.next;
				count++;
			}
			ListNode current=previous.next;
			newNode.next=current;
			previous.next=newNode;
			return head;
		}
	}



	public static void display(ListNode head) {

		if(head==null) {
			return;
		}
		ListNode current=head;
		while(current!=null) {
			System.out.print(current.data + " --> ");
			current=current.next;
		}
		System.out.print(current);
	}




	public static void main(String[] args) {
		// TODO Auto-generated method stub

		ListNode head= new ListNode(1);
		ListNode second=new ListNode(2);
		ListNode third=new ListNode(3);
		ListNode fourth=new ListNode(4);
		ListNode fifth= new ListNode(5);

		head.next=second;
		second.next=third;
		third.next=fourth;
		fourth.next=fifth;

		InsertAtposition insert= new InsertAtposition();
		ListNode insertAt= insert.insertatposition(head,15,2);           ////inserting node at position 2
		InsertAtposition.display(insertAt);                             ////displaying the list.

	}

}
