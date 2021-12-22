
//menu driven program to perform operations on dequeue
#include <stdio.h>
#include<stdlib.h>
#define qs 3
void rinsert(int * ,int *);
void finsert(int *,int *,int *);
void rdelete(int *,int *,int *);
void fdelete(int *,int *,int *);
void display(int *,int ,int );
int main()
{
    int q[qs],r=-1,f=0;
    int ch,i,j;
    while(1)
    {
        printf("\n1.Insert at rear\n2.Insert at front\n3.Delete from rear\n4.Delete from front\n5.Display\n6.exit\nEnter your choice ");
        scanf("%d",&ch);
        switch(ch)
        {
            case 1 : rinsert(q,&r);
                     break;
            case 2 : finsert(q,&r,&f);
                     break;
            case 3 : rdelete(q,&r,&f);
                     break;
            case 4 : fdelete(q,&r,&f);
                     break;
            case 5 : display(q,r,f);
                     break;
            case 6 : exit(0);
        }
    }
    return 0;
}

void rinsert(int * q,int * r)
{
    int ele;
    if(*r == qs)
    {
        printf("\nQueue is full ");
        return;
    }
    printf("\nEnter the element ");
    scanf("%d",&ele);
    ++(*r);
    q[*r]=ele;
}
void finsert(int *q,int *r,int *f)
{
    int ele;
    if((*f) ==0 && (*r)==-1)
    {
        printf("\nEnter the element ");
        scanf("%d",&ele);
        ++(*r);
        q[*r]=ele;
        return;
    }
    if((*f) ==0)
    {
        printf("\nInsertion not possible because it voilates the rules ");
        return;
    }
    printf("\nEnter the element ");
    scanf("%d",&ele);
    --(*f);
    q[*f]=ele;
}
void rdelete(int *q,int *r,int *f)
{
    if((*r) == -1)
    {
        printf("\nQueue is empty ");
        return;
    }
    printf("\nThe deleted element is %d ",q[*r]);
    (*r)--;
}

void fdelete(int *q,int *r,int *f)
{
    if((*f) > (*r))
    {
        printf("\nQueue is empty ");
        return;
    }
    printf("\nThe deleted element is %d ",q[*f]);
    (*f)++;
}

void display(int *q,int r,int f)
{
    int i;
    if(f>r)
    {
        printf("\nQueue is empty ");
        return;
    }
    printf("\nThe elements are ");
    for(i=f;i<=r;i++)
    {
        printf("\n%d",q[i]);
    }
}
