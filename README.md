Algorithms in C
================================================
My takes of **Algorithms in C - Fundamentals, Data Structures, Sorting, Searching (3rd Edition)** book by **Robert Sedgewick**.
It contains code for both the **examples** and the **exercises**.

###Organization

Each *dir* has only the code from the specific chapter.

Each *dir* contains 2 *subdirs*, one with the code for the examples and one with answers for the exercises.

###Compiling

All the programs were compiled with the `-std=c99` flag and should work out of the box.

###Missing & Other 

Some of the answers for particular exercises are missing.
I have omitted exercises which require only a explanatory type of solution or for which I found no value in solving.

**Most of the latest chapters have no exercises**.

Some of the examples are not 100% according to the book, because I tried to make them work in a practical way (are more than only scattered code snippets).
Therefore some examples contain code I have added in order to compile and work with some input.

BUBBLE SORT

#include<stdio.h>
void swap(*a,*b)
{
	int c=*a;
	*a=*b;
	*b=c;
}

void main()
{
	int ar[20],n,i,j;
	printf("Enter size of array:");
	scanf("%d",&n);
	printf("Enter the array:\n");
	for(i=0;i<n;i++)
		scanf("%d",&ar[i]);

	for(i=0;i<n-1;i++)
	{
		for(j=0;j<n-i-1;j++)
	    {
	    	if(ar[j]>ar[j+1])
	    		swap(&ar[j],&ar[j+1]);
	    }
	}

	for(i=0;i<n;i++)
		printf("Sorted array is: %d ",ar[i]);
}


SELECTION SORT

#include <stdio.h>
#include <stdbool.h>

#define MAX 7

int intArray[MAX] = {4,6,3,2,1,9,7};

void printline(int count) {
   int i;
	
   for(i = 0;i < count-1;i++) {
      printf("=");
   }
	
   printf("=\n");
}

void display() {
   int i;
   printf("[");
	
   // navigate through all items 
   for(i = 0;i < MAX;i++) {
      printf("%d ", intArray[i]);
   }
	
   printf("]\n");
}

void selectionSort() {
   int indexMin,i,j;
	
   // loop through all numbers 
   for(i = 0; i < MAX-1; i++) { 
	
      // set current element as minimum 
      indexMin = i;
		
      // check the element to be minimum 
      for(j = i+1;j < MAX;j++) {
         if(intArray[j] < intArray[indexMin]) {
            indexMin = j;
         }
      }

      if(indexMin != i) {
         printf("Items swapped: [ %d, %d ]\n" , intArray[i], intArray[indexMin]); 
			
         // swap the numbers 
         int temp = intArray[indexMin];
         intArray[indexMin] = intArray[i];
         intArray[i] = temp;
      }          

      printf("Iteration %d#:",(i+1));
      display();
   }
}  

void main() {
   printf("Input Array: ");
   display();
   printline(50);
   selectionSort();
   printf("Output Array: ");
   display();
   printline(50);
}


INSERTION SORT

#include <stdio.h>
int main()
{
    int n, i, j, temp;
    int arr[64];
 
    printf("Enter number of elements\n");
    scanf("%d", &n);
 
    printf("Enter %d integers\n", n);
    for (i = 0; i < n; i++)
    {
        scanf("%d", &arr[i]);
    }
    for (i = 1 ; i <= n - 1; i++)
    {
	    j = i;
            while ( j > 0 && arr[j-1] > arr[j])
            {	        
                temp     = arr[j];
                arr[j]   = arr[j-1];
                arr[j-1] = temp;
                j--;
            }
    }
    printf("Sorted list in ascending order:\n");
    for (i = 0; i <= n - 1; i++)
    {
        printf("%d\n", arr[i]);
    }
    return 0;
}


