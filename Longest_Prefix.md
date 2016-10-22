#Find the Longest Common Prefix Among a Set of Strings
		#include<iostream>
		#include<string>
		using namespace std;

		string Prefix(string s1,string s2)
		{
			string common_prefix="";
			int i=0,j=0;
			while(i<s1.length()&&j<s2.length())
			{
				if(s1.at(i)==s2.at(j))
					common_prefix.insert(common_prefix.end(),s1.at(i));
				else if(s1.at(i)!=s2.at(j))
					break;
				i++;
				j++;
			}
			common_prefix.insert(common_prefix.end(),'\0');
			return common_prefix;
		}

		string LongestPrefix(string a[],int start,int end)
		{   string s1,s2,s;
			int mid=(start+end)/2;
			if(start==end)
				 return a[start];
			else
				s1=LongestPrefix(a,0,mid);
				s2=LongestPrefix(a,mid+1,end);
				s=Prefix(s1,s2);

			return s;
		}

		int main()
		{

			int n;
			string A[100];

			cin>>n;
			for(int i=0;i<n;i++)
				cin>>A[i];

			cout<<LongestPrefix(A,0,n-1)<<endl;
		}
