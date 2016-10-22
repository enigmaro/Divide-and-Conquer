#Number of Occurences of An Element in an array

	#include<iostream>
  	using namespace std;
	
  	class Occurences
  	{
  	private: 
		int *SortedArray;
	 	int size;
    		int *occurences;
  	public: 
	 	Occurences(){};
	 	void setArray(int*,int);
	 	int* findOccur(int,int);
	 	void printArray();
  	};
  	void Occurences :: setArray(int *A,int n)
  	{
    		SortedArray=new int[n];
    		occurences=new int[A[n-1]+1];
    		size=n;
    		for(int i=0;i<n;i++)
      		{ SortedArray[i]=A[i];
        	occurences[A[i]]=0;
      		} 
  	}

  	int* Occurences :: findOccur(int start,int end)
  	{  
      		int mid=(start+end)/2;

      		if(SortedArray[start]==SortedArray[end])
          		occurences[SortedArray[start]]=occurences[SortedArray[start]]+end-start+1;        
      		else
          		{ findOccur(start,mid);
            		  findOccur(mid+1,end);
          		}
      		return occurences;
  	}


  	int main()
  	{
	 
      		Occurences F;
      		int a[100],n;
      		int *p;//element;
      		cin>>n;
       		for(int i=0;i<n;i++)
    	  	cin>>a[i];

	     	F.setArray(a,n);
	     	p=F.findOccur(0,n-1);

	     	for(int i=0;i<n;)
        	{ cout<<" Element "<<a[i]<<" : "<<p[a[i]]<<endl;
          	  i+=p[a[i]];
        	}

	     return 0;
	}
	




































