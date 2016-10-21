#Find Floor in a Sorted Array

Given a sorted array and a value x, the floor of x is the largest element in array smaller than or equal to x. Write efficient functions to find floor of x.

	#include<iostream>
	using namespace std;
	
	class FloorElement
	{
	private: 
		int *SortedArray;
		int size;
	public: 
		FloorElement(){};
		void setArray(int*,int);
		int findFloor(float x,int,int);
		void printArray();
	};
	void FloorElement :: setArray(int *A,int n)
	{
   	SortedArray=new int[n];
   	size=n;
   	for(int i=0;i<n;i++)
   		SortedArray[i]=A[i];
	}
	int FloorElement :: findFloor(float x,int start,int end)
	{  
   	int mid=(start+end)/2;
	
   	if(end<start)
		return mid;
   
   	if(SortedArray[mid]==x)
   		return mid;
   	else if(SortedArray[mid]>x)
   	        return findFloor(x,start,mid-1);
   	else if(SortedArray[mid]<x)
   		return findFloor(x,mid+1,end);
	}


	int main()
	{	
    	FloorElement F;
    	int a[100],n,element;
    	cin>>n;
    
    	for(int i=0;i<n;i++)
    	cin>>a[i];

	F.setArray(a,n);
	cin>>element;
	cout<<a[F.findFloor(element,0,n-1)];

	return 0;
	}
