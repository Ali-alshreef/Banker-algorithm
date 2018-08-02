# Banker-algorithm
One of the most famous algorithms in the operating systems is also calculated as a requast for each process and you print it also programmed in Java. I hope you are at the required level and write your comments and observations.

*//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////*

package Banker_Algorithm;
import java.util.Scanner;
import javax.crypto.SecretKeyFactorySpi;
public class banker_algorithm {

    private int need[][],allocate[][],max[][],avail[][],requast[][],val[][],alii[][],vall[][],np,nr,r1,r2,r3,v1,v2,v3,c,ali[][];
     
    private void input(){
     Scanner sc=new Scanner(System.in);
      System.out.println("Welcome to the Bank Algorithm ...... : ");
      System.out.print("Enter no. of processes : ");
     np=sc.nextInt();  //no. of process
      System.out.print("Enter no. of recours : ");
     nr=sc.nextInt();  //no. of resources
  
      System.out.print("Enter no. of R1 : ");
     r1=sc.nextInt();
      System.out.print("Enter no. of R2 : ");
     r2=sc.nextInt();
      System.out.print("Enter no. of R3 : ");
     r3=sc.nextInt();
     
     need=new int[np][nr];  //initializing arrays
     max=new int[np][nr];
     allocate=new int[np][nr];
     avail=new int[np][nr];
      ali=new int [np][nr];
      alii=new int [np][nr];
      requast= new int [np][nr];
      val=new int [np][nr];
      vall= new int [np][nr];
     
     System.out.println("Enter allocation matrix :-");
     for(int i=0;i<np;i++){
         System.out.println("p"+i+"=");
        for(int j=0;j<nr;j++){
        	allocate[i][j]=sc.nextInt(); 
        }
   }
   
   
     System.out.println("Enter max matrix :-");
     for(int i=0;i<np;i++){
           System.out.println("p"+i+"=");
          for(int j=0;j<nr;j++){
         max[i][j]=sc.nextInt(); 
          }
     }
     
     
     for (int n=0 ; n<np;n++){
         v1+=allocate[n][0];
          v2+=allocate[n][1];
          v3+=allocate[n][2];
     }
    v1=r1-v1;
    v2=r2-v2;
    v3=r3-v3;
         vall[0][0]=v1;
          vall[0][1]=v2;
          vall[0][2]=v3;
     avail[0][0]= v1;
     avail[0][1]= v2;
     avail[0][2]= v3;
       System.out.println(); 
     System.out.println(" The Avalibol is : ");
      System.out.println(" X= "+avail[0][0]+" ,   Y= "+avail[0][1]+ " ,   Z= "+avail[0][2]);
      System.out.println();
        
    
     
    }
     
    private int[][] calc_need(){
       for(int i=0;i<np;i++)
         for(int j=0;j<nr;j++) {
          need[i][j]=max[i][j]-allocate[i][j];
         }
    
       return need;
    }
  
    private boolean check(int i){
     
       for(int j=0;j<nr;j++) 
       if(avail[0][j]<need[i][j])
          return false;
    
    return true;
    }
    
    public void isSafe(){
        input();
        calc_need();
       boolean done[]=new boolean[np];
       int j=0;
 
       while(j<np){  //until all process allocated
       boolean allocated=false;
       for(int i=0;i<np;i++)
        if(!done[i] && check(i)){  //trying to allocate
            for(int k=0;k<nr;k++){
            avail[0][k]=avail[0][k]-need[i][k]+max[i][k];
            ali[i][k]=avail[0][k];}
         System.out.println("process  P"+i+" is Safe  ^_^ ");
         allocated=done[i]=true;
               j++;
             } 
       
            if(!allocated) break; 
            }
            if(j==np) { //if all processes are allocate
       System.out.println("\n  The System Is Safe State  ^_^"); 
          result(); 
           requast ();
            }
            else {
        System.out.println(" The System Is UN Safe State  ن_ن");   
       
        System.out.println(); 
        System.out.println("        allocate matrix                    max matrix                        need matrix                      avail matrix       ");
      System.out.println("      |   X   |   Y  |   Z  |          |   X   |   Y  |   Z  |          |   X   |   Y  |   Z  |          |   X   |   Y  |   Z  |  ");
      System.out.println("     ------------------------          -----------------------          -----------------------          ------------------------      ");

      for(int s=0;s<np;s++){
        System.out.print("p"+s+"=  ");
        
        for(int k=0;k<nr;k++){  
      System.out.print(" |   "+allocate[s][k]+" ");}
        System.out.print(" |          ");
        
        for(int k=0;k<nr;k++){  
            System.out.print(" |   "+max[s][k]+" ");}
              System.out.print(" |          ");
              
              for(int k=0;k<nr;k++){  
                  System.out.print(" |   "+need[s][k]+" ");}
                    System.out.print(" |          ");
 
                    for(int k=0;k<nr;k++){  
                        System.out.print(" |   "+ali[s][k]+" ");}
                          System.out.println(" |          ");
              
                          System.out.println("     ------------------------          -----------------------          -----------------------          ------------------------      ");
   
    } 
            }
            }
    
    
    
    public void result()
    {
  
          System.out.println(); 
        System.out.println("        allocate matrix                    max matrix                        need matrix                      avail matrix       ");
      System.out.println("      |   X   |   Y  |   Z  |          |   X   |   Y  |   Z  |          |   X   |   Y  |   Z  |          |   X   |   Y  |   Z  |  ");
      System.out.println("     ------------------------          -----------------------          -----------------------          ------------------------      ");

      for(int s=0;s<np;s++){
        System.out.print("p"+s+"=  ");
        
        for(int k=0;k<nr;k++){  
      System.out.print(" |   "+allocate[s][k]+" ");}
        System.out.print(" |          ");
        
        for(int k=0;k<nr;k++){  
            System.out.print(" |   "+max[s][k]+" ");}
              System.out.print(" |          ");
              
              for(int k=0;k<nr;k++){  
                  System.out.print(" |   "+need[s][k]+" ");}
                    System.out.print(" |          ");
 
                    for(int k=0;k<nr;k++){  
                        System.out.print(" |   "+ali[s][k]+" ");}
                          System.out.println(" |          ");
              
                          System.out.println("     ------------------------          -----------------------          -----------------------          ------------------------      ");
   
    } 
    }
    
    
    public void output()
    {
  
          System.out.println(); 
          System.out.println(); 
          System.out.println("        allocate matrix                    max matrix                        need matrix                      avail matrix                   requast matrix     ");
        System.out.println("      |   X   |   Y  |   Z  |          |   X   |   Y  |   Z  |          |   X   |   Y  |   Z  |          |   X   |   Y  |   Z  |          |   X   |   Y  |   Z  |  ");
        System.out.println("     ------------------------          -----------------------          -----------------------          ------------------------         ------------------------      ");

        for(int s=0;s<np;s++){
          System.out.print("p"+s+"=  ");
          
          for(int k=0;k<nr;k++){  
        System.out.print(" |   "+allocate[s][k]+" ");}
          System.out.print(" |          ");
          
          for(int k=0;k<nr;k++){  
              System.out.print(" |   "+max[s][k]+" ");}
                System.out.print(" |          ");
                
                for(int k=0;k<nr;k++){  
                    System.out.print(" |   "+need[s][k]+" ");}
                      System.out.print(" |          ");
   
                      for(int k=0;k<nr;k++){  
                          System.out.print(" |   "+ali[s][k]+" ");}
                            System.out.print(" |          ");
                            
                            for(int k=0;k<nr;k++){  
                                System.out.print(" |   "+requast[s][k]+" ");}
                                  System.out.println(" |          ");
                
                
                            System.out.println("     ------------------------          -----------------------          -----------------------          ------------------------         -----------------------");
     
      } 
    }
    
    private boolean checkrequast(int i){
       //checking if all resources for ith process can be allocated
       for(int j=0;j<nr;j++) 
       if(val[0][j]<need[i][j])
          return false;
    
    return true;
    }
  
    public void calicrequast(){
        
         boolean done[]=new boolean[np];
       int j=0;
 
       while(j<np){  //until all process allocated
       boolean allocated=false;
       for(int i=0;i<np;i++)
        if(!done[i] && checkrequast(i)){  //trying to allocate
            for(int k=0;k<nr;k++){
            val[0][k]=val[0][k]-need[i][k]+max[i][k];
            ali[i][k]=val[0][k];}
         System.out.println("process  P"+i+" is Safe  ^_^ ");
         allocated=done[i]=true;
               j++;
             } 
       
            if(!allocated) break; 
            }
            if(j==np) { //if all processes are allocate
       System.out.println("\n  The System Is Safe State  ^_^"); 
       output();
       System.out.println("  The process  p " + c +" is exuted  ^_^ ");
       requast();
          
            }
            else {
        System.out.println(" The System Is UN Safe State  ن_ن");   

        System.out.println(); 
      System.out.println("       allocate matrix              max matrix                   need matrix                avail matrix                  requast matrix ");
    System.out.println("      |  X  |  Y  |  Z  |        |  X  |  Y  |  Z  |          |  X  |  Y  |  Z  |           |  X  |  Y  |  Z  |          |  X  |  Y  |  Z  |");
      for(int s=0;s<np;s++){
      System.out.print("p"+s+"=  ");
      
      for(int k=0;k<nr;k++){  
    System.out.print(" | "+allocate[s][k]+" | ");}
      System.out.print("      ");
      
      for(int k=0;k<nr;k++){  
    System.out.print(" | "+max[s][k]+" |  ");}
              System.out.print("      ");

  for(int k=0;k<nr;k++)  {
    System.out.print(" | "+need[s][k]+" | ");}
          System.out.print("      ");


      for(int k=0;k<nr;k++)  {
    System.out.print(" | "+ali[s][k]+" |  ");}
              System.out.print("      ");
              
              for(int k=0;k<nr;k++)  {
    System.out.print(" | "+requast[s][k]+" |  ");}
              System.out.println("  ");
   System.out.println("    ------------------------     ----------------------     ------------------------      ------------------------      ------------------------");
 
  }
      System.out.println("  The process  p " + c +" is not exuted  ^_^ ");
    }
    }
    
      public void requast (){
          Scanner sc=new Scanner(System.in);
          
         // for (int r=0;r<np; r++){
          System.out.print(" Enter The number of process  p = ");
        c=sc.nextInt();
        if (c==0 || c==1||c==2||c==3||c==4){
            System.out.print("enter the requast of this process  p"+c);
       
            for (int i=c ; i<c+1;i++){
                for(int y=0 ; y<3;y++)
            requast[i][y]=sc.nextInt();
            }
       
            for (int i =c ; i<c+1; i++){
if (requast[i][0] <= vall[0][0] && requast[i][1] <= vall[0][1] && requast[i][2] <= vall[0][2]){
         //   for ( int n=0 ; n<nr; n++){
if(requast[i][0] <= need[i][0] && requast[i][1] <= need[i][1] && requast[i][2] <= need[i][2]){
                    val[0][0]=vall[0][0]-requast[i][0];
                     val[0][1]=vall[0][1]-requast[i][1];
                      val[0][2]=vall[0][2]-requast[i][2];
                      need[i][0]=need[i][0]-requast[i][0];
                     need[i][1]=need[i][1]-requast[i][1];
                      need[i][2]=need[i][2]-requast[i][2];
                       allocate[i][0]=allocate[i][0]+requast[i][0];
                     allocate[i][1]=allocate[i][1]+requast[i][1];
                      allocate[i][2]=allocate[i][2]+requast[i][2];
                    
         vall[0][0]= val[0][0];
               vall[0][1]= val[0][1];
                 vall[0][2]= val[0][2];
            System.out.println(" The new avilibol  = "+val[0][0]+" "+val[0][1]+" "+val[0][2]);
    System.out.println(" The new need  = "+need[i][0]+" "+need[i][1]+" "+need[i][2]);
      System.out.println(" The new allocate  = "+allocate[i][0]+" "+allocate[i][1]+" "+allocate[i][2]);
                     
      calicrequast( );
            
             
    }else {
                    System.out.println(" Soory ICan't Running , Becouse The requast > need ");
                    } 
}else {
                    System.out.println(" Soory ICan't Running , Becouse The requast > avalibol OR need ");
                }
            }
     
        } else {
            System.out.println(" soory ::: this process not foind ");
        }
      }
     // }
      
      
    public static void main(String[] args) {
       new banker_algorithm ().isSafe();
        
    } 
}
