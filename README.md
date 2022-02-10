# Queues-using-linked-lists
#include<stdio.h>
#include<stdlib.h>
struct queue
{
    int data;
    struct queue *next;
};
typedef struct queue node;
node *front=NULL,*rear=NULL;
void enque(int x)
{
    node *new;
    new=(node *)malloc(sizeof(node));
    new->data=x;
    new->next=NULL;
    if(rear==NULL&&front==NULL)
    {
        front=new;
        rear=new;
    }
    else
    {
        rear->next=new;
        rear=new;
    }
}
int deque()
{
    node *temp;
    int x;
    if(front==NULL)
    {
        printf("Queue underflown\n");
    }
    else
    {
        x=front->data;
        if(front==rear)
        {
            front=rear=NULL;
        }
        else
        {
            temp=front;
            front=front->next;
            free(temp);
        }
        return x;
    }
}
void display()
{
    node *temp;
    if(front==NULL)
    {
        printf("Queue is empty");
    }
    else
    {
        temp=front;
        while(temp!=NULL)
        {
            printf("%d\t",temp->data);
            temp=temp->next;
        }
    }
}
void main()
{
    int ch,x;
    while(1)
    {
        printf("\n1.Enque\n2.Deque\n3.Display\n4.Exit");
        printf("\nEnter your choice");
        scanf("%d",&ch);
        switch(ch)
        {
            case 1: printf("\nEnter the element to insert ");
                    scanf("%d",&x);
                    enque(x);
                    break;
            case 2: x=deque();
                    if(x==-1)
                    {
                        printf("Queue is underflown");
                    }
                    else
                    {
                        printf("Queue element deleted %d",x);
                    }
                    break;
            case 3: printf("\nThe elements in queue are ");
                    display();
                    break;
            case 4: exit(0);
        }
    }
}

OUTPUT:

1.Enque
2.Deque
3.Display
4.Exit
Enter your choice1

Enter the element to insert 5

1.Enque
2.Deque
3.Display
4.Exit
Enter your choice1

Enter the element to insert 7

1.Enque
2.Deque
3.Display
4.Exit
Enter your choice1

Enter the element to insert 3

1.Enque
2.Deque
3.Display
4.Exit
Enter your choice1

Enter the element to insert 4

1.Enque
2.Deque
3.Display
4.Exit
Enter your choice3

The elements in queue are 5	7	3	4	
1.Enque
2.Deque
3.Display
4.Exit
Enter your choice2
Queue element deleted 5
1.Enque
2.Deque
3.Display
4.Exit
Enter your choice1

Enter the element to insert 6

1.Enque
2.Deque
3.Display
4.Exit
Enter your choice3

The elements in queue are 7	3	4	6	
1.Enque
2.Deque
3.Display
4.Exit
Enter your choice4
