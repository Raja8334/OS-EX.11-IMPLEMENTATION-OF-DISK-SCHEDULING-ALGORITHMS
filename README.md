# OS-EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS

## DISK SCHEDULING FIRST COME FIRST SERVE

# AIM:
To write a program for the first come first serve method of disc scheduling.
# ALGORITHM:
* Initialize an array RQ to store disk requests and variables n, TotalHeadMoment, and initial.
* Prompt the user to input the number of requests (n) and the request sequence (RQ).
* Prompt the user to input the initial head position (initial).
* Calculate TotalHeadMoment by iterating through the requests, adding the absolute difference between each request and the current head position to TotalHeadMoment, and updating the head position.
* Print the TotalHeadMoment as the result of the FCFS disk scheduling.
# PROGRAM:
```python
#include <stdio.h>
#include <stdlib.h>
int main()
{
int RQ[100],i,n,TotalHeadMoment=0,initial;
printf ("Enter the number of Requests\n");
scanf("%d",&n);
printf("Enter the Requests sequence\n");
for(i=0;i<n;i++)
{
scanf("%d",&RQ[i]);
}
printf("Enter initial head position\n");
scanf("%d",&initial);

for(i=0;i<n;i++)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
printf("Total head moment is %d",TotalHeadMoment);
return 0;
}
```
# OUTPUT:
![image](https://github.com/Raja8334/OS-EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS/assets/120719634/d7a6ff9f-b311-47d1-aada-959df61128aa)


# RESULT:
Thus, the implementation of the C program for first come first serve disc scheduling has been successfully executed.

## DISK SCHEDULING SHORTEST SEEK TIME FIRST
# AIM:
To write a program for the shortest seek time first method of disc scheduling.

# ALGORITHM:
* Initialize variables and arrays for requests, total head movement, initial head position, and a counter.
* Input the number of requests, the request sequence, and the initial head position from the user.
* Find the nearest request by looping through the requests, calculating the absolute difference from the current head position, and updating the head position based on the closest request.
* Repeat this process until all requests are processed, marking completed requests with a large number.
* Print the total head movement as the result of the SSTF disk scheduling.
# PROGRAM:
```python
#include<stdio.h>
#include<stdlib.h>
int main()
{
int RQ[100],i,n,TotalHeadMoment=0,initial,count=0;
printf("Enter the number of Requests\n");
scanf("%d",&n);
printf("Enter the Requests sequence\n");
for(i=0;i<n;i++)
scanf("%d",&RQ[i]);
printf("Enter initial head position\n");
scanf("%d",&initial);
while(count!=n)
{
int min=1000,d,index;
for(i=0;i<n;i++)
{
d=abs(RQ[i]-initial);
if(min>d)
{
min=d;
index=i;
}
}
TotalHeadMoment=TotalHeadMoment+min;
initial=RQ[index];
RQ[index]=1000;
count++;
}
printf("Total head movement is %d",TotalHeadMoment);
return 0;
}
```
# OUTPUT 
![image](https://github.com/Raja8334/OS-EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS/assets/120719634/564217a8-c2d2-4768-89ed-9ddbf65eb631)
# RESULT
Thus, the implementation of the C program for shortest seek time first disc scheduling has been successfully executed.
## DISK SCHEDULING SCAN OR ELEVATOR
# AIM:
To write a program for the scan method of disc scheduling.

# ALGORITHM:
* Initialize variables and arrays for requests, total head movement, initial head position, disk size, and the head movement direction.
* Input the number of requests, the request sequence, initial head position, total disk size, and the head movement direction from the user.
* Sort the request array in ascending order to facilitate the SCAN algorithm.
* Find the index where the initial head position lies in the sorted request array and calculate head movements in the chosen direction (high or low) while iterating through the requests.
* Calculate the total head movement by summing the absolute differences in head positions and print the result as the total head movement for the SCAN disk scheduling algorithm.
# PROGRAM:
```python
#include<stdio.h>
#include<stdlib.h>
int main()
{
int RQ[100],i,j,n,TotalHeadMoment=0,initial,size,move;
printf("Enter the number of Requests\n");
scanf("%d",&n);
printf("Enter the Requests sequence\n");
for(i=0;i<n;i++)
scanf("%d",&RQ[i]);
printf("Enter initial head position\n");
scanf("%d",&initial);
printf("Enter total disk size\n");
scanf("%d",&size);
printf("Enter the head movement direction for high 1 and for low 0\n");
scanf("%d",&move);
for(i=0;i<n;i++)
{
for(j=0;j<n-i-1;j++)
{
if(RQ[j]>RQ[j+1])
{
int temp;
temp=RQ[j];
RQ[j]=RQ[j+1];
RQ[j+1]=temp;
}
}
}
int index;
for(i=0;i<n;i++)
{
if(initial<RQ[i])
{
index=i;
break;
}
}
if(move==1)
{
for(i=index;i<n;i++)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
// last movement for max size
TotalHeadMoment=TotalHeadMoment+abs(size-RQ[i-1]-1);
initial = size-1;
for(i=index-1;i>=0;i--)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
}
else
{
for(i=index-1;i>=0;i--)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
TotalHeadMoment=TotalHeadMoment+abs(RQ[i+1]-0);
initial =0;
for(i=index;i<n;i++)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
}
printf("Total head movement is %d",TotalHeadMoment);
return 0;
}
```
# OUTPUT
![image](https://github.com/Raja8334/OS-EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS/assets/120719634/61890077-2a63-46c4-929b-b9568a5af39e)
# RESULT
Thus, the implementation of the C program for SCAN disc scheduling has been successfully executed.
## DISK SCHEDULING C-SCAN
# AIM:
To write a program for the c-scan method of disc scheduling.

# ALGORITHM:
* Initialize variables and arrays for requests, total head movement, initial head position, disk size, and the head movement direction.
* Input the number of requests, the request sequence, initial head position, total disk size, and the head movement direction from the user.
* Sort the request array in ascending order to facilitate the SCAN algorithm.
* Find the index where the initial head position lies in the sorted request array and calculate head movements in the chosen direction (high or low) while iterating through the requests.
* Calculate the total head movement by summing the absolute differences in head positions and print the result as the total head movement for the SCAN disk scheduling algorithm.
# PROGRAM 
```python
#include<stdio.h>
#include<stdlib.h>
int main()
{
    int RQ[100],i,j,n,TotalHeadMoment=0,initial,size,move;
    printf("Enter the number of Requests\n");
    scanf("%d",&n);
    printf("Enter the Requests sequence\n");
    for(i=0;i<n;i++)
     scanf("%d",&RQ[i]);
    printf("Enter initial head position\n");
    scanf("%d",&initial);
    printf("Enter total disk size\n");
    scanf("%d",&size);
    printf("Enter the head movement direction for high 1 and for low 0\n");
    scanf("%d",&move); 
    // logic for C-Scan disk scheduling 
        /*logic for sort the request array */
    for(i=0;i<n;i++)
    {
        for( j=0;j<n-i-1;j++)
        {
            if(RQ[j]>RQ[j+1])
            {
                int temp;
                temp=RQ[j];
                RQ[j]=RQ[j+1];
                RQ[j+1]=temp;
            }
        }
    }
    int index;
    for(i=0;i<n;i++)
    {
        if(initial<RQ[i])
        {
            index=i;
            break;
        }
    } 
    // if movement is towards high value
    if(move==1)
    {
        for(i=index;i<n;i++)
        {
            TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
            initial=RQ[i];
        }
        //  last movement for max size 
        TotalHeadMoment=TotalHeadMoment+abs(size-RQ[i-1]-1);
        /*movement max to min disk */
        TotalHeadMoment=TotalHeadMoment+abs(size-1-0);
        initial=0;
        for( i=0;i<index;i++)
        {
             TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
             initial=RQ[i]; 
        }
    }
    // if movement is towards low value
    else
    {
        for(i=index-1;i>=0;i--)
        {
            TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
            initial=RQ[i];
        }
        //  last movement for min size 
        TotalHeadMoment=TotalHeadMoment+abs(RQ[i+1]-0);
        /*movement min to max disk */
        TotalHeadMoment=TotalHeadMoment+abs(size-1-0);
        initial =size-1;
        for(i=n-1;i>=index;i--)
        {
             TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
             initial=RQ[i]; 
        }
    }
    printf("Total head movement is %d",TotalHeadMoment);
    return 0;
}
```
# OUTPUT
![image](https://github.com/Raja8334/OS-EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS/assets/120719634/bdb93da1-3ede-458a-ae0d-6c15815894d4)
# RESULT
Thus, the implementation of C-SCAN Disk scheduling algorithm in C programming is done successfully.
DISK SCHEDULING LOOK
# AIM:
To write a program for the look method of disc scheduling.

# ALGORITHM:
* Initialize variables and arrays for requests, total head movement, initial head position, disk size, and the head movement direction.
* Input the number of requests, the request sequence, initial head position, total disk size, and the head movement direction from the user.
* Sort the request array in ascending order to facilitate the LOOK algorithm.
* Find the index where the initial head position lies in the sorted request array and calculate head movements in the chosen direction (high or low) while iterating through the requests.
* Calculate the total head movement by summing the absolute differences in head positions and print the result as the total head movement for the LOOK disk scheduling algorithm.
# PROGRAM
#include<stdio.h>
#include<stdlib.h>
int main()
{
int RQ[100],i,j,n,TotalHeadMoment=0,initial,size,move;
printf("Enter the number of Requests\n");
scanf("%d",&n);
printf("Enter the Requests sequence\n");
for(i=0;i<n;i++)
scanf("%d",&RQ[i]);
printf("Enter initial head position\n");
scanf("%d",&initial);
printf("Enter total disk size\n");
scanf("%d",&size);
printf("Enter the head movement direction for high 1 and for low 0\n");
scanf("%d",&move);
for(i=0;i<n;i++)
{
for(j=0;j<n-i-1;j++)
{
if(RQ[j]>RQ[j+1])
{
int temp;
temp=RQ[j];
RQ[j]=RQ[j+1];
RQ[j+1]=temp;
}
}
}
int index;
for(i=0;i<n;i++)
{
if(initial<RQ[i])
{
index=i;
break;
}
}
if(move==1)
{
for(i=index;i<n;i++)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
for(i=index-1;i>=0;i--)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
}
else
{
for(i=index-1;i>=0;i--)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
for(i=index;i<n;i++)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
}
printf("Total head movement is %d",TotalHeadMoment);
return 0;
}
# OUTPUT
![image](https://github.com/Raja8334/OS-EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS/assets/120719634/38563779-bddf-4289-a687-fabecaf23aed)
# RESULT
Thus, the implementation of the C program for LOOK disc scheduling has been successfully executed.
DISK SCHEDULING C-LOOK
# AIM:
To write a program for the c-look method of disc scheduling.

# ALGORITHM:
* Initialize variables and arrays for requests, total head movement, initial head position, disk size, and the head movement direction.
* Input the number of requests, the request sequence, initial head position, total disk size, and the head movement direction from the user.
* Sort the request array in ascending order to facilitate the LOOK algorithm.
* Find the index where the initial head position lies in the sorted request array and calculate head movements in the chosen direction (high or low) while iterating through the requests.
*Calculate the total head movement by summing the absolute differences in head positions and print the result as the total head movement for the LOOK disk scheduling algorithm.
# PROGRAM:

```python
#include<stdio.h>
#include<stdlib.h>
int main()
{
    int RQ[100],i,j,n,TotalHeadMoment=0,initial,size,move;
    printf("Enter the number of Requests\n");
    scanf("%d",&n);
    printf("Enter the Requests sequence\n");
    for(i=0;i<n;i++)
     scanf("%d",&RQ[i]);
    printf("Enter initial head position\n");
    scanf("%d",&initial);
    printf("Enter total disk size\n");
    scanf("%d",&size);
    printf("Enter the head movement direction for high 1 and for low 0\n");
    scanf("%d",&move); 
    // logic for C-look disk scheduling 
        /*logic for sort the request array */
    for(i=0;i<n;i++)
    {
        for( j=0;j<n-i-1;j++)
        {
            if(RQ[j]>RQ[j+1])
            {
                int temp;
                temp=RQ[j];
                RQ[j]=RQ[j+1];
                RQ[j+1]=temp;
            }
        }
    }
    int index;
    for(i=0;i<n;i++)
    {
        if(initial<RQ[i])
        {
            index=i;
            break;
        }
    } 
    // if movement is towards high value
    if(move==1)
    {
        for(i=index;i<n;i++)
        {
            TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
            initial=RQ[i];
        } 
        for( i=0;i<index;i++)
        {
             TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
             initial=RQ[i]; 
        }
    }
    // if movement is towards low value
    else
    {
        for(i=index-1;i>=0;i--)
        {
            TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
            initial=RQ[i];
        } 
        for(i=n-1;i>=index;i--)
        {
             TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
             initial=RQ[i]; 
        }
    }
    printf("Total head movement is %d",TotalHeadMoment);
    return 0;
}
```
# OUTPUT
![image](https://github.com/Raja8334/OS-EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS/assets/120719634/e212bab8-b771-4acd-ae17-030eb6d89736)
# RESULT
Thus, the implementation of C-look Disk scheduling algorithm in C programming is done successfully.


