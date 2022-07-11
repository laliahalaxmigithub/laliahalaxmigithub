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
	


--->
