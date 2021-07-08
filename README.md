#include<stdio.h>
#include<stdlib.h>
int main()
{
    int a[10],n,i;
    printf("enter n size\n");
    scanf("%d",&n);
    printf("enter value to array\n");
    for(i=0;i<n;i++)
    scanf("%d",&a[i]);
    printf("elements before sorting\t");
    for(i=0;i<n;i++)
    printf("%d\n",a[i]);
    Quick_sort(0,n-1,a);
    printf("elements after sorting\n");
    for(i=0;i<n;i++)
    printf("%d",a[i]);
}
Quick_sort(int lb,int ub,int a[])
{
    if(lb<ub)
    {
        int p;
        p=partition(lb,ub,a);
        Quick_sort(lb,ub,a);
        Quick_sort(p+1,ub,a);
    }
}
int partition(int lb,int ub,int a[])
{
    int left,right,t;
    left=lb;
    right=ub;
    int pivot=a[lb];
    while(left<right)
    {
        while(left<=ub && a[left]<=pivot)
        {
            left++;
        }
        while(right>=lb && a[right]>pivot)
        {
            right--;
            if(left< right)
            {
                t=a[left];
                a[left]=a[right];
                a[right]=t;
            }
        }
        t=a[lb];
        a[lb]=a[right];
        a[right]=t;
        return right;
    }
}
