#include <stdio.h>
#include <unistd.h>
#include  <sys/types.h>

int calculate_Sum(int i, int n){
    int j, sum=0;
    for(j=i; j<n; j++){
	    sum +=  1;
    }
    return sum;
}

int main() {
 	int cpid;
	int i,j;
 	int fSum;
	int sum1=0, sum2=0;
    
    for(i=0;i<2;i++){
	    cpid= fork();
        if(cpid==0){
           //printf("CPID in IF : %d \n",cpid);
           sum1 += calculate_Sum(0,25);
           fSum +=  sum1;
        }
        else{
            // printf("CPID in ELSE : %d \n",cpid);
	     	sum2 = calculate_Sum(0,25);
		    fSum +=  sum2 ;
            // printf("final sum:%d \n" ,fSum);
        }
	    wait(NULL);
   }
      printf("SUM is %d \n" , fSum);
   return 0;
}