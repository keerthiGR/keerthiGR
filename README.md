import java.util.*;

class IplRes{
	
	 String name;
	 int points;
	 int[] result;
	 
	 public IplRes(String name, int points, int[] result) {
		
		this.name = name;
		this.points = points;
		this.result = result;
		
	 }
	 public String getName() {
		return name;
	 }
	
	 public int getPoints() {
		return points;
	 }

	 public int[] getResult() {
		return result;
	 }	 
}
public class Ipl {

	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in);
		
		List<IplRes> team=new ArrayList<>();
		List<IplRes> conLoss=new ArrayList<>();
		
		int[] r1 = {1,1,0,0,1},    //1 represents win 0 represents loss
			  r2 = {1,0,0,1,1},
			  r3 = {1,0,1,0,0},
			  r4 = {1,1,0,1,0},
			  r5 = {0,1,1,0,0},
			  r6 = {0,1,1,0,1},
			  r7 = {0,1,0,1,0},
			  r8 = {1,0,0,0,0},
			  r9 = {0,0,1,0,1},
			  r10= {0,1,0,1,1};
		
		team.add(new IplRes("GT",20,r1));       
		team.add(new IplRes("LSG",18,r2));
		team.add(new IplRes("RR",18,r3));
		team.add(new IplRes("DC",14,r4));
		team.add(new IplRes("RCB",14,r5));
		team.add(new IplRes("KKR",12,r6));
		team.add(new IplRes("PBKS",12,r7));
		team.add(new IplRes("SRh",12,r8));
		team.add(new IplRes("CSK",8,r9));
		team.add(new IplRes("MI",8,r10));
		
	   System.out.println("enter the number of consecutive losses which you want ");
	   int n=sc.nextInt();
	   
	   for(IplRes res : team) {
		   
		   int count=0;
		   int[] arr=res.getResult();
		   for(int loss : arr) {
			   
			   int r=(loss==0) ? count++ : (count=0);
			   
			   if(count==n) {
				   
				   conLoss.add(res);
				   break;
			   }
		   }
	    }
	    System.out.println("consecutively lossed teams are");
	    int totalteam=0;
	    double points=0;
	    
	    for(IplRes res : conLoss) {
	    	
	    	totalteam++;
	    	points=points+res.getPoints();
	    	System.out.println(res.getName());
	    }
	    String avg=(totalteam!=0) ? "average="+points/totalteam : "No team with Consecutive losses";
	    System.out.println(avg);
	}

}
