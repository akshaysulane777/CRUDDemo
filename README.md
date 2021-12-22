# CRUDDemo
Simple program by using CRUD operation by using java collection 


import java.util.*;

class Student{
	private int srNo;
	private String sName;
	private int sMarks;
	
	Student(int srNo, String sName, int sMarks){
	this.srNo = srNo;
	this.sName = sName;
	this.sMarks = sMarks;
	}
	
	public int getsrNo()
	{
		return srNo;
	}
	public int getsMarks()
	{
		return sMarks;
	}
	public String getsName()
	{
		return sName;
	}
	public String toString()
	{
		return srNo+" "+sName+" " +sMarks;
	}	
}

class CRUDDemo{
	public static void main(String[] args)
	{
		//Collection<Employee> c = new ArrayList<Employee>();
		   List<Student> c = new ArrayList<Student>();
		Scanner s = new Scanner(System.in);
		Scanner s1 = new Scanner(System.in);
		int ch;
		do{
			System.out.println("1.INSERT");
			System.out.println("2.DISPLAY");
			System.out.println("3.SEARCH");
			System.out.println("4.DELETE");
			System.out.println("5.UPDATE"); 
			System.out.print("Enter your Choice : ");
			ch = s.nextInt();
			
				switch(ch)
				{
					case 1:
					System.out.print("Enter Studnet Roll Number : ");
					int srNo = s.nextInt();
					
					System.out.print("Enter Studnet Name : ");
					String sName = s1.nextLine();
					
					System.out.print("Enter Studnet Marks : ");
					int sMarks = s.nextInt();
					
					c.add(new Student(srNo,sName,sMarks));
					break;
					
					
					case 2:
					System.out.println("----------------------------------------");
					Iterator<Student> i = c.iterator();
					while(i.hasNext())
					{
						Student e = i.next();
						System.out.println(e);
					}
					System.out.println("----------------------------------------");
					break;
				
					case 3:
					boolean found = false;
					System.out.print("Enter Studnet Roll Number to Search : ");
					 srNo = s.nextInt();
					System.out.println("----------------------------------------");
					i = c.iterator();
					while(i.hasNext()){
						Student e = i.next();
						
						if(e.getsrNo() == srNo)
						{
							System.out.println(e);
							found = true;
						}	
					}
					if(!found)
					{
						System.out.println("Record Not found");
					}
					System.out.println("----------------------------------------");
					break;
					
					case 4:
					found = false;
					System.out.print("Enter Studnet Roll Number to Search : ");
					  srNo = s.nextInt();
					System.out.println("----------------------------------------");
					i = c.iterator();
					while(i.hasNext()){
						Student e = i.next();
						
						if(e.getsrNo() == srNo)
						{
							i.remove();
							found = true;
						}	
					}
					if(!found)
					{
						System.out.println("Record Not found");
					}
					else
					{
						System.out.println(" Record is Deleted successfully ...! ");
					}
					System.out.println("----------------------------------------");
					break;
					case 5:
					found = false;
					System.out.print("Enter Studnet Roll Number to Update : ");
					  srNo = s.nextInt();
					  
					  ListIterator<Student>li = c.listIterator();
						
						while(li.hasNext())
						{
						Student e = li.next();
						
						if(e.getsrNo() == srNo)
						{
							System.out.print("Enter new Name :");
							sName = s1.nextLine();
							
							System.out.print("Enter new Marks : ");
							sMarks = s.nextInt();
							li.set(new Student(srNo,sName,sMarks));
							found = true;
						}	
					}
					if(!found)
					{
						System.out.println("Record Not found");
					}
					else
					{
						System.out.println(" Record is Updated successfully ...! ");
					}
					break;
				}
			}while(ch!= 0);
	}		
}
