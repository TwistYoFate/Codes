#include<iostream>
#include<bitset>
#include<stdio.h>
#include<algorithm>
#define lp(i,n) for(i=0;i<n;i++)  
#define ll long 
using namespace std;

//this is max heapify, for min_heapify select smallest instead of largest value ( i.e. parent)
void max_heapify(int **a,int parent,int n){
    //left node
    int left=parent*2;

    //right node
    int right=parent*2+1;

    //largest/smallest
    int largest;

    //checking left child
    if(left<=n && (*a)[left]>=(*a)[parent])
        largest=left;
    else
        largest=parent;

    //checking right child
    if(right<=n && (*a)[right]>=(*a)[largest])
        largest=right;

    if(largest!=parent){
        //swap{
        int k;
        k=(*a)[largest];
        (*a)[largest]=(*a)[parent];
        (*a)[parent]=k;
        //}
        max_heapify(a,largest,n);
    }
}

void max_heap(int **a,int n){
    int i;
    for(i=n/2;i>=1;i--)
        max_heapify(a,i,n);
}

void printArray(int arr[],int n){
    int i;
    for(i=1;i<=n;i++){
        cout<<arr[i]<<" ";
    }
    cout<<endl;
}
  
int main(){
    int a[8]={0,1,4,3,7,8,9,10};
    int *p;
    p=a;
    max_heap(&p,7);
    printArray(a,7);
return 0;
}