# Lru
lru page replacement
#include<stdio.h>
int search(int);
int get(int,int); 

int a[100],b[10];
int n,f;
int  main()
{


	int i=0,j=0,count=0,k;
	printf("\nenter no of references:");
	scanf("%d",&n);
	printf("\n enter references");
	for(i=0;i<n;i++)
	{
		scanf("%d",&a[i]);
	}
	printf("\nenter no of frames");
	scanf("%d",&f);
	for(i=0;i<f;i++)
	{
		b[i]=-1;
	}
	//***********logic strats here********************
	for(i=0;i<n;i++)
	{
		if(j<f)
		{
				if(b[j]==-1)
					{
						k=search(a[i]);
						
						if(k<f)
						{
							continue;
						}
						else{
						
					b[j]=a[i];
					j++;
					count++;
				}
					}
		}
		else
			{
			k=search(a[i]);
			if(k==f)
			{
						int w[10],z=0,h,r;
						for(z=0;z<f;z++)
						{
							w[z]=get(b[z],i);
						
						}
						h=w[0];
						for(r=1;r<f;r++)
						{
							if(w[r]<h)
								h=w[r];
						}
						for(r=0;r<f;r++)
						{
							if(h==w[r])
								{
								b[r]=a[i];
								count++;
								break;	
								}
						}
						
						
					
			} 
			else if(k<f)
			{
				continue;
			}
				
			}
			
	}
	printf("\n the no of page faults in LRU=%d",count);
return 0;
}
int search(int m)
{
	int i;
	for(i=0;i<f;i++)
	{
		if(b[i]==m)
		
			return i;
	}
		
	return f;

}
int get(int p,int q)
{

	int j;
	for(j=q-1;j>-1;j--)
	{
		if(p==a[j])
			return j;
			
	}

}
