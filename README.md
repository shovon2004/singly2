#include<stdio.h> 
#include<stdlib.h> 
#include<string.h> 
 
struct node{ 
    char name[30]; 
    int data; 
    struct node *next; 
}; 
 
int main() 
{ 
    struct node *head,*second,*third; 
    head=(struct node*)malloc(sizeof(struct node)); 
    strcpy(head->name, "Sakib"); 
    head->data = 2; 
    head->next =NULL; 
 
    second=(struct node*)malloc(sizeof(struct node)); 
    strcpy(second->name, "Rafin"); 
    second->data = 3; 
    second->next = NULL; 
 
    third=(struct node*)malloc(sizeof(struct node)); 
    strcpy(third->name, "Mehedi"); 
    third->data = 5; 
    third->next = NULL; 
 
    head->next = second; 
    second->next = third; 
 
    //Insert a newnode in 1st position---- 
    struct node *newnode; 
    newnode=(struct node*)malloc(sizeof(struct node)); 
    strcpy(newnode->name,"Rajat"); 
    newnode->data = 1; 
    newnode->next = NULL; 
 
    newnode->next = head; 
    head=newnode; 
 
    //Insert a newnode in last position---- 
    struct node *lastnode; 
    lastnode=(struct node*)malloc(sizeof(struct node)); 
    strcpy(lastnode->name, "Mozahid"); 
    lastnode->data = 6; 
    lastnode->next = NULL; 
 
    struct node *temp; 
    temp= head; 
 
    while(temp->next!=NULL) 
    { 
        temp=temp->next; 
    } 
 
    temp->next=lastnode; 
 
    struct node *Print; 
    Print = head; 
 
    while(Print!=NULL) 
    { 
        printf("%s\n", Print->name); 
        printf("%d\n", Print->data); 
        printf("\n"); 
        Print = Print->next; 
    } 
 
    //Insert a newnode in any position---- 
    struct node *body; 
    body=(struct node*)malloc(sizeof(struct node)); 
    strcpy(body->name, "Akash"); 
    body->data = 4; 
    body->next = NULL; 
 
    printf("please Enter a position to insert a node:"); 
 
    struct node *copy1; 
    copy1=head; 
 
    int i,n; 
    scanf("%d",&n); 
    printf("\n"); 
    copy1=head; 
 
    for(i=1;i<n-1 && copy1!=NULL;i++) 
    { 
        copy1=copy1->next; 
    } 
 
    body->next=copy1->next; 
    copy1->next=body; 
 
    temp = head; 
    while(temp!=NULL) 
    { 
        printf("%s\n",temp->name); 
        printf("%d\n",temp->data); 
        printf("\n"); 
        temp = temp->next; 
    } 
 
    //Delete a node from 1st position.... 
    printf("Start Deleting....\n\n"); 
    temp=head; 
    head=head->next; 
    free(temp); 
    temp=NULL; 
 
    //Delete a node from last position.... 
    temp=head; 
    while(temp->next->next!=NULL) 
    { 
        temp=temp->next; 
    } 
    free(temp->next); 
    temp->next=NULL; 
 
    //Delete a node from last position in other way... 
    struct node *temp1; 
    temp=head; 
    temp1=head; 
    while(temp->next!=NULL) 
    { 
        temp1=temp; 
        temp=temp->next; 
    } 
    free(temp); 
    temp1->next=NULL; 
    temp=NULL; 
 
    Print = head; 
    while(Print!=NULL) 
    { 
        printf("%d\n",Print->data); 
        printf("\n"); 
        Print = Print->next; 
    } 
 
    //Delete a node from any index.... 
    printf("Enter the position to delete the node: "); 
    scanf("%d",&n); 
    printf("\n"); 
 
    temp=head; 
    for(i=1;i<n-1 && temp!=NULL;i++) 
    { 
        temp=temp->next; 
    } 
    struct node *hold; 
    hold=temp->next->next; 
    free(temp->next); 
    temp->next=hold; 
 
    Print = head; 
    while(Print!=NULL) 
    { 
        printf("%d\n",Print->data); 
        printf("\n"); 
        Print = Print->next; 
    } 
 
    //Searching Data and counting node... 
    int search=0,count=0; 
    printf("Enter a data to search:"); 
    scanf("%d",&n); 
    temp=head; 
    while(temp!=NULL) 
    { 
        count++; 
        if(temp->data == n) 
        { 
            search=1; 
        }temp=temp->next; 
    } 
    printf("Total node = %d\n",count); 
    if(search==1){printf("data exist\n");} 
    else{printf("Data not exist\n");} 
 
    return 0; 
 
}
