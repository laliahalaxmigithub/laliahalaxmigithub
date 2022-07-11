public class employee {
	
	static int diff(int array[],int N, int M) {
		int result = Integer.MAX_VALUE;
		Arrays.sort(array);
		for(int i=0; i<=N-M; i++)
			 result = Math.min(result, array[i+M-1]-array[i]);
		return result;	
	}
	
    static int findelement(int res, int array[], int N, int M)
    {
      int result =Integer.MAX_VALUE;
      for(int i=0; i<=N; i++)
      {
    	  result = Math.min(result, array[i+M-1]-array[i]);
    	  if(res==result)
    		  return i;
      }
      return 0;
    }

    public static void main(String[] args)
    {
    	int array[]= {7980,22349,999,2799,229900,11101,9999,2195,9800,4999};
    	String items[]= {"mi band: 999"," sandwich toster: 2195", " cult pass: 2799", "scale: 4999",
    			"fitbit plus: 7980","microwave oven: 9800", 
    			"alexa: 9999","digital camera: 11101", " ipads: 22349", " mcbook pro:  229900"};
    	int N=array.length;
    	System.out.println("enter no of emp");
    	Scanner s= new Scanner(System.in);
    	int M=s.nextInt();
    	int result=diff(array,N,M);
    	System.out.println("Number of emp :" +M);
    	int startindex=findelement(result,array,N,M);
    	
    	for(int i=startindex;i<startindex+M;i++)
    		System.out.println(items[i]);
    	{
    		System.out.println("\n");
    	System.out.println("diff b/w  choosen goodies with hp and lp :" +result);
    		
    	}
    }
}
	

import java.io.*;
import java.util.*;
class Item {
  String name;
  int price;

  public Item(String name, int price) {
    this.name = name;
    this.price = price;
  }

  public String toString() { 
      return this.name + ": " + this.price;
  }
}

public class Main {
  public static void main(String[] args) throws Exception {
    FileInputStream fis=new FileInputStream("input.txt");       
    Scanner sc=new Scanner(fis);
    int number_of_employees = Integer.parseInt(sc.nextLine().split(": ")[1]);
    sc.nextLine(); sc.nextLine(); sc.nextLine();

    ArrayList<Item> goodies_items = new ArrayList<Item>();

    while(sc.hasNextLine())  
    {
      String current[] = sc.nextLine().split(": ");
      goodies_items.add(new Item(current[0], Integer.parseInt(current[1])));
    }
    sc.close();

    Collections.sort(goodies_items, new Comparator<Item>(){
      public int compare(Item a, Item b) { 
        return a.price - b.price; 
      } 
    });

    int min_diff = goodies_items.get(goodies_items.size()-1).price;
    int min_index = 0;
    for(int i=0;i<goodies_items.size()-number_of_employees+1;i++) {
      int diff = goodies_items.get(number_of_employees+i-1).price-goodies_items.get(i).price;

      if(diff<=min_diff) {
        min_diff = diff;
        min_index = i;
      }
    }
    
    

    FileWriter fw = new FileWriter("output.txt");
    fw.write("The goodies selected for distribution are:\n\n");
    for(int i=min_index;i<min_index + number_of_employees; i++) {
      fw.write(goodies_items.get(i).toString() + "\n");
    }

    fw.write("\nAnd the difference between the chosen goodie with highest price and the lowest price is " + min_diff);
	  fw.close();
  }
}
--->
