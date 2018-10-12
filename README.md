# OS3


#include <stdio.h>
#include <stdlib.h>
#include <sys/wait.h>

#include <sys/type.h>
#include<unistd.h>

int calculateSum(int arr[], int s, int e){
   int sum=0;
   for(int i=s;i<e;i++)
    sum=sum+arr[i];
 
    return sum;
 } 

int main(){
  arr[1000];
  for(int i=0;i<1000;i++){
   arr[i]=i;
  }


  int pid1[2],pid2[2],pid3[2],pid4[2],pid5[2],pid6[2],pid7[2],pid8[2],pid9[2],pid10[2];
  
  pipe(pid1); 
  pipe(pid2);
  pipe(pid3);
  pipe(pid4);
  pipe(pid5);  
  pipe(pid6);
  pipe(pid7);
  pipe(pid8);
  pipe(pid9);
  pipe(pid10);
  
  int get1,get2,get3,get4,get5,get6,get7,get8,get9,get10=0;


  int s1,s2,s3,s4,s5,s6,s7,s8,s9,s10=0;
  int total=0;
 
  int cpid=fork();
  if(cpid==0){
        s1=calculateSum(arr,0,100);
        write(pid1[1],&s1,sizeof(s1)); 

        close (pid1[1]);
        exit(0);
        
 }
  else{
     int cpid=fork();
        if(cpid==0){
        s2=calculateSum(arr,100,200);
        write(pid2[1],&s2,sizeof(s2)); 

        close (pid2[1]);
        exit(0);
        }
       
     else{
     int cpid=fork();
        if(cpid==0){
        s3=calculateSum(arr,200,300);
        write(pid3[1],&s3,sizeof(s3)); 

        close (pid3[1]);
        exit(0);
        }
     
        else{
        int cpid=fork();
        if(cpid==0){
        s4=calculateSum(arr,300,400);
        write(pid4[1],&s4,sizeof(s4)); 

        close (pid4[1]);
        exit(0);
         }

         else{
          int cpid=fork();
          if(cpid==0){
          s5=calculateSum(arr,400,500);
          write(pid5[1],&s5,sizeof(s5)); 

          close (pid5[1]);
          exit(0);
          }
            else{
            int cpid=fork();
            if(cpid==0){
            s6=calculateSum(arr,500,600);
            write(pid6[1],&s6,sizeof(s6)); 

            close (pid6[1]);
            exit(0);
             }

              else{
              int cpid=fork();
              if(cpid==0){
              s7=calculateSum(arr,600,700);
              write(pid7[1],&s7,sizeof(s7)); 

              close (pid7[1]);
              exit(0);
               }

                else{
                int cpid=fork();
                if(cpid==0){
                s8=calculateSum(arr,700,800);
                write(pid8[1],&s8,sizeof(s8)); 

                close (pid8[1]);
                exit(0);
                }

                  else{
                  int cpid=fork();
                  if(cpid==0){
                  s9=calculateSum(arr,800,900);
                  write(pid9[1],&s9,sizeof(s9)); 
             
                  close (pid9[1]);
                  exit(0);
                   }
                  
                     else{
                     int cpid=fork();
                     if(cpid==0){
                     s10=calculateSum(arr,900,1000);
                     write(pid10[1],&s10,sizeof(s10)); 
             
                     close (pid10[1]);
                     exit(0);
                  }
                   else{
                     for(int i=0;i<10;i++){
                     wait(); }
                  
                   read(pid1[0],&get1,sizeof(get1));
                   total=total+get1; 
                  
                   read(pid2[0],&get2,sizeof(get2));
                   total=total+get2;
                   
                   read(pid3[0],&get3,sizeof(get3));
                   total=total+get3;

                   read(pid4[0],&get4,sizeof(get4));
                   total=total+get4;

                   read(pid5[0],&get5,sizeof(get5));
                   total=total+get5;

                   read(pid6[0],&get6,sizeof(get6));
                   total=total+get6;
 
                   read(pid7[0],&get7,sizeof(get7));
                   total=total+get7;

                   read(pid8[0],&get8,sizeof(get8));
                   total=total+get8;

                   read(pid9[0],&get9,sizeof(get9));
                   total=total+get9;

                   read(pid10[0],&get10,sizeof(get10));
                   total=total+get10; 

                   printf("Sum of 1000 elements of is %d\n", total);
                  }
                 }    
                }  
               }             
              }             
             }
            }
           }
          }
         }
}


