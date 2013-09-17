Lab-08-Assignment
=================

Software which explains the synchronization between process
 
 // Finalised solution for the problem.......
//DINING PHILOSOPHER PROBLEM

#include<stdio.h>
char state[10],self[10],spoon[10];
void test(int k)     // Function test for checking which philosopher is eating......
{
  if((state[(k+4)%5]!='e')&&(state[(k+1)]!='e'))
  {
  state[k]='e';
  self[k]='s';
  spoon[k]='n';
  spoon[(k+4)%5]='n';
  }
 }
  void pickup(int i)   // Function pickup for spoons.....
  {
  state[i]='h';
  test(i);
  if(state[i]=='h')
  self[i]='w';
  }
  void putdown(int i)  // Function for putting down Spoon.....
  {
  state[i]='t';
  spoon[i]='s';
  spoon[i-1]='s';
  test((i+4)%5);
  test((i+1)%5);
   }
   main()               // here is main function....
  {
   int ch,a,n,i;
   printf("\nDINING PHILOSOPHERS PROBLEM :");
   for(i=0;i<5;i++)
    {
    state[i]='t';
    self[i]='s';
    spoon[i]='s';
     }
    printf("\nInitial state of each philosopher :");
    printf("\nPHIL NO:\tTHINK\t\tSTATUS\t\tSPOON");
                 for(i=0;i<5;i++)
    printf("\n%d\t\t%c\t\t%c\t\t%c",i+1,state[i],self[i],spoon[i]);
    printf("\n1.EXIT\n2.HUNGRY\n3.THINKING");
    printf("\nEnter your choice :");
    scanf("%d",&ch);
    while(ch!=1)
     {
    switch(ch)


   {
 case 1:
 return 0;
 case 2:
 printf("\nEnter which philosopher is hungry :");
scanf("%d",&n);
 pickup(n-1);
 break;
 case 3:
 printf("\nEnter which philosopher is thinking :");
 scanf("%d",&n);
 putdown(n-1);
 break;
 }
 printf("State of each philosopher :");
 printf("\nPHIL NO:\tTHINK/EAT\tSTATUS\t\tSPOON");
 for(i=0;i<5;i++)
printf("\n%d\t\t%c\t\t%c\t\t%c",i+1,state[i],self[i],spoon[i]);
printf("\n1.EXIT\n2.HUNGRY\n3.THINKING");
 printf("\nEnter your choice :");
 scanf("%d",&ch);
 }
}
